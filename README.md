# family-dashboard

Public Skylight family dashboard. Static HTML on GitHub Pages. Allowlisted artifact only.

## Remote content update

Any authorized AgentCore agent can publish a new dashboard from this repository. A later content change does not need a socket or USB.

- Source: https://github.com/scottishramp/family-dashboard, branch `main`. GitHub Pages serves the repository root.
- Site: https://scottishramp.github.io/family-dashboard/
- Page: https://scottishramp.github.io/family-dashboard/index.html
- Manifest: https://scottishramp.github.io/family-dashboard/manifest.json
- Keep `contentUrl` at `https://scottishramp.github.io/family-dashboard/index.html`.
- Routine: change `index.html`, set manifest `sha256` to that file's SHA256, and set `version` to the first 14 hex characters of that hash. Commit `index.html` and `manifest.json`. Non-force push to `main`. Leave `.nojekyll` in place.
- Verify: the Pages build for that commit is `built`, then an HTTPS GET of the manifest and the page returns 200 and the fetched HTML SHA256 equals manifest `sha256`.
- Viewer v1.2.1 uses the one-time public hosted viewer configuration. While the screen is in the foreground it polls about once a minute and keeps the last good snapshot. A cached page can remain on screen when the network is down. The on-screen `v2` marker is a display revision only, not a connectivity signal.
- Medicine records and checkbox state stay on the device. Publishing this site does not control the Android device. Reboot and startup behavior are not yet tested.
- Rollback: publish the previous `index.html` bytes again with a manifest whose `sha256` matches those bytes and whose `contentUrl` is unchanged.

## First successful publish from this repo

On 2026-11-08 at 8:31 PM America/Chicago, a repo-bound cloud agent pushed commit `666684c89a471b40f5344b491d7fd7550c2f5488` to `main` without force. Pages build `1353080654` built that commit. The live page SHA256 was `477c470c6535004e2dcb055ea48d2e644eeb07e2aa5d9afa8fefb0c8c176aca5`.

`X-Accepted-GitHub-Permissions` is the permission an endpoint requires. It is not the permission the token holds. Repository API flags that read false on this app token were not an actual `git push` denial. Do not ask for more user permissions from that header or those flags alone.

The display marker `v2` is the website revision after that first publish. This file does not claim the tablet has shown `v2`. Check the device screen after the public page is live.
