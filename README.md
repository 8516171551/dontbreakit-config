# dontbreakit-config

**This repository is intentionally public, and must stay public.**

It is not source code. It is the public web host for three things the
*Don't Break It* iOS app and Apple both require to be readable by anyone,
with no login:

| File | Who reads it | What breaks if this repo goes private |
|---|---|---|
| `privacy.md` | Apple App Review, and any user who taps Privacy Policy | The Privacy Policy URL registered in App Store Connect returns 404. **App Review rejects the submission.** |
| `support.md` | Apple App Review, and any user who taps Support | The Support URL registered in App Store Connect returns 404. **App Review rejects the submission.** |
| `version.json` | The app itself, on every launch | The mandatory-update check cannot fetch its config, so the update gate stops working for new installs. |

The exact URLs Apple has on file are:

- Privacy: `https://github.com/8516171551/dontbreakit-config/blob/main/privacy.md`
- Support: `https://github.com/8516171551/dontbreakit-config/blob/main/support.md`

The app fetches:

- `https://raw.githubusercontent.com/8516171551/dontbreakit-config/main/version.json`

## What is NOT here

No game source code. No API keys, tokens, certificates or credentials — the
full commit history has been scanned and has never contained any. The game's
source lives only on the developer's machine and is not published anywhere.

The one piece of personal data here is the support contact email, which Apple
requires to be reachable on a public support page.

## Changing the update gate

`minimumVersion` is the oldest build allowed to run. Raising it forces every
player below that version to update before they can play, so raise it only
once the new build is actually live on the App Store — otherwise you lock
players out of a version they cannot yet download.

`updateURL` is where the UPDATE NOW button sends them. It points at the App
Store product page. If it is omitted entirely, the app falls back to the same
App Store URL compiled into `UpdateGate.appStoreURL`.
