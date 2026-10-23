# Local Agent Notes

- Keep build artifacts outside the source tree. The current configured build directory is `../build_upbge`.
- Include standard headers directly when using their declarations. For example, include `<cstdint>` when using `uint32_t`.

## Remotes

- `origin` is the fork, `https://github.com/buddha314/upbge`. All pushes go here.
- `upstream` is `https://github.com/UPBGE/upbge`. It is fetch-only (push URL is `no_push`). Never push to it.
- `master` tracks `origin/master`. Local changes live as ordinary commits on `master` on top of upstream.

## Syncing with upstream and keeping local changes

Upstream history is integrated with merge commits, not rebases, so local commits keep their hashes and the fork never needs a force push.

1. Start from a clean tree: `git status` shows nothing to commit, and `master` matches `origin/master`.
2. Bring in upstream, either way:
   - Locally: `git fetch upstream`, then `git merge upstream/master`.
   - Or with GitHub's "Sync fork" button on the fork, then `git pull origin master` locally.
3. Resolve conflicts. For each local change listed below, check whether upstream already made the same fix. If it did, take upstream's version and drop ours. Otherwise keep ours.
4. Rebuild: `make -j"$(nproc)" -k install` in `../build_upbge`. `-k` reports every error in one pass. Missing standard includes (like the `<cstdint>` case) are the most common break after a sync. Fix them by including the header directly in the file that uses it.
5. Commit any fixes the merge needed, then `git push origin master`.

## Local changes carried on top of upstream

Keep this list current when adding or dropping a local change.

- `source/blender/draw/intern/gpu_modifiers/*.hh`: `#include <cstdint>` added to headers that use `uint32_t`. Drop this once upstream includes it.
- `AGENTS.md` (this file) and `doc/workstation_extensions.md`: local documentation, not in upstream.

## System install

- `/usr/local/bin/upbge` is a symlink to `../build_upbge/bin/blender-launcher`, and the system menu entry `/usr/local/share/applications/org.upbge.UPBGE.desktop` runs `upbge`. A successful `make install` updates both. No copy step is needed.
- Restart UPBGE after a rebuild, because the binary is replaced in place.
- To verify, run `upbge --version`. Its `build hash` should equal `git rev-parse --short=12 HEAD`, and `build branch` should not say `(modified)`. A build made with uncommitted changes shows the previous commit's hash plus `(modified)`.
- `~/.local/bin/blender` is a separate stock Blender 5.3 install, not UPBGE. Leave it alone.
