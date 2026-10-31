# SpinDuo Privacy Policy

**Last updated: October 31, 2026**

This policy describes how the SpinDuo iPhone and iPad app handles information when you use its record-player interface, bundled demo music, and optional Apple Music, Spotify, and YouTube features. Available features may vary by app version and your connected accounts.

## Information handled by SpinDuo

SpinDuo does not require a separate SpinDuo account or operate an app backend for uploading your music library, playback history, or account credentials. The app handles the information needed to display your chosen records and control playback:

- **Preferences and restoration:** selected music-service tab, playback and display settings, and supported last-record restoration information. A playback bookmark can contain service, album, playlist and track identifiers, side mode, side and playback position. These are stored in the app's local preferences.
- **Music and video metadata:** album, playlist and track identifiers, titles, artists or channel information, artwork or thumbnail addresses, durations, queue order and playback state. This information is used to browse, display and play your selection. Loaded metadata and image caches are used on the device; network and operating-system caches may also retain data.
- **Authorization information:** service access tokens and, where provided, refresh tokens or saved sign-in information, so an account you connect can remain connected without signing in each time.
- **Local diagnostics:** timestamps, app version/build, loading stages, timing, playback state transitions, request counts and error categories/codes, used to investigate failures.

Bundled demo playback does not require connecting a music-service account. Connecting a service is optional, but the connected features need the relevant permission, network access and provider account eligibility.

## Apple Music

If you choose Apple Music, SpinDuo uses Apple's MusicKit authorization and services to check access/subscription capability, browse your authorized library albums and playlists, search the catalog, retrieve record details and artwork, and control playback and the selected queue.

Requests and playback communicate with Apple through its frameworks and services. Apple handles your Apple Account and subscription; SpinDuo does not ask for or store your Apple Account password. Music identifiers and supported playback bookmarks may be saved locally for restoration. Artwork requests also communicate with the relevant image host.

Apple's handling of Apple Music activity is described in [Apple Music & Privacy](https://www.apple.com/legal/privacy/data/en/apple-music/).

## Spotify

Spotify sign-in uses Spotify's authorization flow. SpinDuo requests playback-control permission and, for library browsing, read access to saved library content and private playlists. It uses the Spotify Web API for album/playlist metadata and the installed Spotify app through App Remote for playback commands and state.

SpinDuo receives OAuth tokens rather than your Spotify password. Its Spotify access/refresh tokens are stored in the device Keychain, with the app's token item configured for access while the device is unlocked and for this device only. Saved authorization may be refreshed or reused to connect and load the library when you open the Spotify tab.

Spotify and its artwork hosts receive requests needed for these features. Spotify remains responsible for its account, streaming and related activity. See the [Spotify Privacy Policy](https://www.spotify.com/legal/privacy-policy/).

## Google authorization and YouTube user data

Connecting a Google Account is optional. SpinDuo uses YouTube API Services to browse playlists owned by your account, retrieve playlist items and video metadata, search YouTube videos when you submit a search, and check whether selected videos allow embedded playback. Google user data handled for these features includes playlist and video identifiers, titles, thumbnail addresses, pagination information, the search text you submit, and the video or playlist you select. Playback also involves player state and playback interactions.

Starting with version 1.0 (49), Google authorization uses AppAuth with Google's authorization service and requests only the read-only YouTube scope, `https://www.googleapis.com/auth/youtube.readonly`. It does not request the OpenID, email, or profile identity scopes. The app does not ask for or receive your Google password. It receives OAuth authorization information, including access tokens and refresh tokens when Google supplies them. Requests to browse or search do not edit, delete, or upload your YouTube videos or playlists. Earlier app versions used Google Sign-In; permissions previously granted in your Google Account can remain until you revoke them there.

### Sharing, transfer, and disclosure of Google user data

The current integration uses these recipients and purposes:

- **Google and YouTube:** your device sends authorization and token-refresh requests to Google's OAuth services, and sends the access token and requested playlist/video identifiers or search text to the YouTube Data API to perform the feature you request. Google's YouTube player and thumbnail/image hosts receive the video/playlist or image requests needed to display and play your selection. These requests also expose ordinary network information, including your IP address, to the receiving service.
- **YouTube's embedded player and its service providers:** video playback uses YouTube's visible embedded player in an Apple WebView. The player can receive playback interactions, requested content, device/app/browser information, and network information. It can use cookies or similar website storage and display advertising under Google's service rules. Loading the player contacts YouTube even without connecting an account for playlist browsing. OAuth authorization for the Data API does not itself sign the WebView into YouTube.
- **Apple's device services:** iOS provides the system authorization browser, Keychain storage, WebView, clipboard, and other operating-system facilities on your device. Apple may receive diagnostics or TestFlight feedback that you choose to share under Apple's distribution and device settings; the app does not routinely send your fetched Google playlists or OAuth tokens to an Apple analytics service.
- **Lumalilt maintainers and the support service you choose:** if you intentionally send a screenshot, report, or message containing Google-related information, its recipients receive that information to respond to your request. A public GitHub issue is visible publicly. Do not include tokens, private playlists, or other sensitive information in a public report. Use the contact guidance below to request a private contact method first.

SpinDuo does not send Google OAuth tokens, fetched playlist/video lists, or YouTube search text to a Lumalilt backend. It does not transfer one service's library or credentials to Apple Music, Spotify, or another music service. Lumalilt does not sell Google user data, send it to advertising platforms or data brokers, use it to target advertising, or use it to train artificial-intelligence models. YouTube's own embedded-player advertising and processing are separate and are described above. Maintainers do not routinely have access to your on-device Google authorization or private library; they receive only information you deliberately share through support or distribution feedback.

See the [Google Privacy Policy](https://policies.google.com/privacy) and [YouTube Terms of Service](https://www.youtube.com/t/terms) for Google's processing. You can review and revoke SpinDuo's access through [Google Account third-party connections](https://myaccount.google.com/connections).

### Protection of sensitive Google user data

- Google authorization, token refresh, YouTube API requests, and native thumbnail requests use HTTPS to protect data in transit. AppAuth uses the system authentication browser, authorization-state validation, and the PKCE code-verifier mechanism to protect the native OAuth exchange; the app does not collect your Google password or embed a client secret.
- Saved authorization state, including supplied access/refresh tokens, is stored in the iOS Keychain. The app configures its current Google token item for access only while the device is unlocked and for this device only. Tokens are sent to the YouTube Data API in an Authorization header rather than a request URL.
- Native YouTube API browsing uses an ephemeral network session and bypasses local response caching. Fetched lists and search results are held in app memory rather than written to a Lumalilt database. The native thumbnail loader uses HTTPS and an ephemeral session without persistent cookie, credential, or URL-cache storage; decoded images have a bounded in-memory cache.
- The app's diagnostics are intended for operational state and error categories, not Google passwords, OAuth tokens, or raw private playlist contents. Copying diagnostics is an explicit action and does not automatically upload the report.

These controls do not erase or isolate data held by Google, prevent all access on a compromised device, or make YouTube's WebView storage ephemeral. The embedded player uses normal website-data storage, and its cookies, caches, and provider processing follow platform and Google controls. No security mechanism provides an absolute guarantee.

### Retention and deletion of Google user data

**Authorization:** the current Keychain authorization state is retained so the app can restore your connection and refresh access while you use the YouTube features. There is no app-defined fixed expiry for that saved state. **Sign out locally** clears the in-memory authorization and requests deletion of the current Keychain item. If iOS cannot delete that item, the app records a signed-out marker to prevent its restoration until an explicit reconnect; this is not a guarantee that every stored credential byte has been erased. The current app does not read, migrate, or reuse legacy Google Sign-In token items from older versions, and current local sign-out is not an erasure mechanism for those older items.

**Browsing, search, and playback:** playlist/video browsing lists are retained in app memory while the browser is in use and are replaced or cleared by reconnecting, local sign-out, navigation, or ending the app process, depending on the list. Search text and results are reset when you change or clear the search, leave its view, or change authorization. A selected playback queue, record metadata, or decoded-thumbnail cache may remain in memory after local sign-out until replaced or the app process ends. These in-memory copies have no separate fixed retention period. Ordinary preferences such as your selected service and display settings remain until changed or the app's data is removed. WebView cookies, website data, operating-system logs, and data retained by Google are separate from these app lists.

To stop access and remove the local data described above:

1. In SpinDuo's **Records > YouTube** area, use **Sign out locally**. This clears the current browsing lists and requests deletion of the current Google authorization item. Stop YouTube playback and close SpinDuo completely to release any remaining in-memory queue, metadata, thumbnails, and diagnostic buffer. Use **Clear** in search or **Clear diagnostics** in Settings to clear those items without ending the app process.
2. Open [Google Account third-party connections](https://myaccount.google.com/connections), select SpinDuo, and remove its access. You can also use [Google's permissions page](https://security.google.com/settings/security/permissions). This revokes the Google grant, including older permissions that may remain from earlier app versions. Local sign-out alone does not revoke it. Revocation prevents subsequent authorized access under that grant; it does not itself erase already-loaded content from the running app, so also complete the local steps above. The app checks authorization when restoring or making authorized requests, not continuously while it is closed.
3. To remove app-container preferences and website data, use iOS Settings to **Delete App**, rather than offloading it. Uninstalling alone must not be relied on to revoke Google access or erase all Keychain items, backups, system logs, or copies you exported or shared. Revoke access through Google even if you have removed SpinDuo.
4. To request deletion of Google-related information you previously sent to maintainers, use the contact guidance below, identify the support request, and ask for deletion without posting additional sensitive data publicly. Such information is retained only as needed to handle the request, investigate security issues, meet applicable legal obligations, or establish and defend legal claims; there is no fixed automatic deletion period. Public GitHub records, provider-held copies, or reports sent through Apple are also subject to the respective service's controls.

SpinDuo does not provide a developer-hosted Google-data account or library database to delete. Deleting SpinDuo data or revoking its access does not delete your Google Account, YouTube playlists/videos, Google-held activity, or provider backups. Use Google's and YouTube's account, history, and deletion controls for data they hold. The current local sign-out control is not a one-step deletion of every category listed here.

## Diagnostics and information you choose to share

The in-app diagnostic buffer keeps up to 100 recent events in memory. It is intended to record operational details rather than passwords, OAuth tokens or raw private library contents. Some operational events also use Apple's system logging.

Settings provides **Copy diagnostics** and **Clear diagnostics**. Copy places the current report on the system clipboard; it does not automatically send it to the developer. Clipboard handling, including any synchronization, is controlled by your operating system. Review a report before sending it through a support channel. Clear removes the in-app buffer, not reports you already copied/shared or separate operating-system logs.

If you send a report or message to the maintainers, they receive the information you include and use it to respond or investigate the problem. The communication service you choose also handles that information. No fixed retention period for support correspondence is promised here; ask the recipient about a report you have shared.

## Analytics, advertising and other recipients

The app does not include a dedicated behavioral-analytics or crash-reporting service, an advertising SDK, or an in-app purchase flow. This does not mean that connected providers, embedded YouTube content, Apple distribution/TestFlight services or the operating system collect no information. Their processing is governed by their own policies and your settings.

Network requests go to the selected services and artwork hosts to provide the requested features. SpinDuo does not upload one connected service's library or credentials to another as a library-sync feature. Selecting a service does not erase data the providers already hold.

## Your choices and retention

- **Apple Music:** review or withdraw SpinDuo's music permission in system Settings. Provider features may stop working when permission is removed.
- **Google/YouTube:** use **Sign out locally** in the YouTube area to clear that local sign-in and the loaded browsing lists. Local sign-out does not revoke Google's account grant; use the Google account controls linked above to revoke access.
- **Spotify:** review/remove SpinDuo's access using Spotify's account app-access controls. Disconnecting App Remote is not the same as revoking the account grant or erasing saved tokens.
- **Restoration:** turn off **Load last record** to stop automatic restoration. This switch is not an erase-all-data control.
- **Diagnostics:** clear the in-app buffer, and separately delete any reports or clipboard copies you saved or shared.

Local preferences remain until changed or the relevant app data is removed. Loaded in-memory lists and caches can be replaced or cleared as the app runs or exits; system-managed caches, website data and logs follow system/service storage behavior. Removing the app ordinarily removes its app-container data, but do not rely on uninstalling alone to revoke provider grants or erase Keychain credentials, backups or copies you shared. Use provider account controls to revoke access. Provider-side history and retention are governed by the providers.

The app does not ask for microphone recordings, camera access, contacts or precise location for these features. Services can still infer approximate location from network information. Protect your device and accounts: platform protections and encrypted network connections reduce risk but cannot guarantee absolute security.

## Questions, requests and changes

For questions about this policy or how to reach the SpinDuo maintainers, use the [SpinDuo project issues page](https://github.com/lumalilt/SpinDuo/issues). This is a public channel: do not post credentials, private playlists, personal information or unredacted diagnostics. Ask for a private contact method before sharing sensitive information.

Depending on where you live, you may have rights concerning personal information. Requests about information held by Apple, Spotify or Google should also be directed to those providers using their privacy controls. SpinDuo cannot delete their account records or history.

This policy may be updated as the app changes. The date above identifies the current revision.
