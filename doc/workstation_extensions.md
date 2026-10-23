# Workstation Blender extensions

This is a deduplicated inventory of extensions installed in the user's Blender 5.3 and UPBGE 5.4 profiles, recorded on 2026-10-12. The version/profile columns describe what was found on this workstation; they are not a compatibility guarantee for other Blender builds.

Blender and UPBGE keep separate user profiles. Installing an extension in one does not install or enable it in the other. On another workstation, install the needed entries from the sources below in each application where they are wanted. Prefer each extension's repository or official download over copying profile folders.

## Extension inventory

| Extension | Installed profile(s) | Installed version | Where to get it |
| --- | --- | --- | --- |
| [Bagapie](https://www.f12studio.fr/bagapiev6) | UPBGE 5.4 | 11.0.11 | F12Studio, the creator's site. Install from the creator's download/account flow. |
| [BlenderKit](https://www.blenderkit.com/) | Blender 5.3, UPBGE 5.4 | 3.21.3-261002 | BlenderKit's extension repository is already configured in both profiles. The add-on is also available from the BlenderKit site. |
| [engon](https://superhivemarket.com/products/engon) | UPBGE 5.4 | 1.12.0 | Superhive order/download page, or polygoniq's extension repository: `https://extensions.polygoniq.com/api/v1/extensions`. |
| [Extra Curve Objects](https://extensions.blender.org/add-ons/extra-curve-objects/) | Blender 5.3, UPBGE 5.4 | 0.2.0 | Blender Extensions website; searchable as “Extra Curve Objects” in Get Extensions. |
| [Extra Mesh Objects](https://extensions.blender.org/add-ons/extra-mesh-objects/) | Blender 5.3, UPBGE 5.4 | 0.4.1 | Blender Extensions website; searchable as “Extra Mesh Objects” in Get Extensions. Includes the Rock Generator mesh operator. |
| [MCP](https://www.blender.org/lab/mcp-server/) | Blender 5.3, UPBGE 5.4 | 1.0.3 in Blender 5.3; 1.0.0 in UPBGE | Blender Lab's MCP Server page. Add the Blender Lab extension repository (`https://lab.blender.org/`) and install MCP. The profiles currently use different versions. |
| [MPFB](http://static.makehumancommunity.org/mpfb.html) | Blender 5.3 | 2.0.18 | MakeHuman Community's MPFB page or the Blender Extensions listing. Not installed in UPBGE. |

## Enablement found in the profiles

These are the enabled extension add-ons recorded in each profile when inspected:

- Blender 5.3: BlenderKit, Extra Mesh Objects, MCP, and MPFB.
- UPBGE 5.4: Bagapie, BlenderKit, engon, and MCP.
- Extra Curve Objects and Extra Mesh Objects are installed in UPBGE's extension folders, but were not enabled in its saved preferences. Enable them from **Preferences → Get Extensions → Installed** if needed.

The MCP package is the same extension identity in both profiles, but the versions differ. For a clean setup, use the Blender Lab repository to install the current compatible version rather than copying one profile's package over the other.

## Manual add-ons found in the older Blender 5.1 profile

These are traditional add-ons in `~/.config/blender/5.1/scripts/addons/`, not extensions from the 5.3/5.4 profiles above:

| Add-on | Where to get it |
| --- | --- |
| Blosm | [Blosm documentation](https://github.com/vvoovv/blosm/wiki/Documentation) and its linked download page. |
| Poly Haven Assets | [Poly Haven add-on guide](https://docs.polyhaven.com/en/guides/blender-addon); the downloadable add-on is distributed through the account/patronage options described there. |
| Copy - Paste Image | The installed folder is a local legacy add-on. Its exact upstream/version was not identifiable from the folder name alone; use the original download source or a compatible replacement rather than copying it blindly. |

## Recreating the setup

1. Install each extension in the Blender or UPBGE profile where you want it. Blender's Extensions system stores both the package and enablement state per profile.
2. Enable the add-on after installation. In particular, enable Extra Mesh Objects to get **Shift+A → Mesh → Rock Generator**.
3. Install traditional add-ons separately through **Preferences → Add-ons → Install from Disk**. Do not copy the complete `userpref.blend`; it contains profile-specific preferences and repository credentials.
4. Add repository credentials, such as the Superhive token, interactively on the destination workstation. Do not put tokens in this document or in source control.

The inventory records extension packages and install sources, not asset-library downloads, user preferences, API credentials, or Blender's built-in add-ons.
