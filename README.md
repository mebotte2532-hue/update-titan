# TiTaN Self - Railway

## MajidAPI configuration

The downloader uses MajidAPI as the primary web service.

Set this Railway variable:

```text
MAJID_API_TOKEN=YOUR_MAJIDAPI_TOKEN
```

Optional:

```text
MAJID_API_BASE=https://api.majidapi.ir
```

Do **not** put the real token inside `self.py`, `Self.zip`, or GitHub.

## Railway deployment

1. Push this project to GitHub.
2. Create a new Railway project from the repository.
3. Keep the existing start command/Procfile.
4. Open **Variables** for the Railway service.
5. Add `MAJID_API_TOKEN` with your real token.
6. Redeploy.
7. Watch the deployment logs. The self source prints its fix version when it starts.

The project keeps the existing architecture: `bot.py` prepares `source/Self.zip`, extracts it for each account, and launches `self.py`.

## Downloader

### Instagram profile

```text
.iginfo username
```

Uses:

```text
GET /instagram/profile?username=USERNAME&token=TOKEN
```

### Instagram manual downloader

```text
.igdl URL
```

Uses the documented Instagram downloader endpoint with `out=url`.

### Automatic social-link downloader

Sending a supported social URL directly from the self account triggers the automatic downloader. Instagram uses the dedicated MajidAPI endpoint; the generic social endpoint is attempted first for other supported platforms.

### App search

```text
.app APP_NAME
```

Uses the MajidAPI Farsroid search/download endpoints.

`.apk` has been removed from the self source and helper.

## Updated features

- Per-user PV lock instead of a global PV lock.
- Block/unblock accepts reply, username and numeric ID.
- LOVE/ENEMY rules now compare `from_user.id`, not `chat.id`.
- LOVE/ENEMY lists persist in `feature_state.json`.
- Spam tasks can be stopped/cancelled and report status.
- Monshi2 supports enable/disable, channels/groups, custom text, photo, list, removal and membership confirmation buttons.
- Lock commands have safer validation and status output.

## Important

MajidAPI currently documents Instagram download/profile endpoints and Farsroid app search/download endpoints. Its public service page also publishes request-rate tiers, so API limits can still affect a deployed self even when the code is correct.
