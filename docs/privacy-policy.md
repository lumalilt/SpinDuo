# SpinDuo Privacy Policy

**Last updated: October 26, 2026**

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

## Google sign-in and YouTube

SpinDuo uses Google Sign-In and the YouTube Data API to connect an account and browse owned playlists and their video metadata. It requests the read-only YouTube scope, `https://www.googleapis.com/auth/youtube.readonly`. These browsing requests do not edit, delete or upload videos or playlists. Google Sign-In manages saved authorization and token refresh on the device; its SDK may also handle the account information supplied through Google's sign-in flow.

Video playback uses YouTube's visible embedded player in a WebView. Loading that player contacts YouTube even if you have not connected an account for playlist browsing. The player, thumbnails and sign-in services can receive information such as the requested video/playlist, playback interactions, app/browser information and network information, including your IP address. The WebView uses its normal website-data storage; provider cookies or similar technologies may be used. YouTube may show advertising under its own service rules. SpinDuo does not represent the player as tracking-free or as native YouTube Music library access.

See the [Google Privacy Policy](https://policies.google.com/privacy) and [YouTube Terms of Service](https://www.youtube.com/t/terms). You can review and revoke account access in [Google Account third-party connections](https://myaccount.google.com/connections).

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
