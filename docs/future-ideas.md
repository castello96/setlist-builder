# Set List Builder — Future Ideas

Nov 22, 2026 · @Nick

## Up next: bulk lyrics import

Import the lyrics files already in Google Drive (exported as .txt or .docx) in one go. Each file is matched to a catalog song by filename, and the files that don't match are listed so the user can match them by hand. This is part 2 of the lyrics work.

## Idea 1: Export a set list to a Spotify playlist

**Status: built** (Spotify button in a setlist; setup under Band settings → Spotify).

The user signs into Spotify from the app, then taps one button to turn the current set list into a playlist with every song in set order. Spotify's Web API supports this: it has endpoints to search the catalog, create a playlist, and add tracks to it ([migration guide](https://developer.spotify.com/documentation/web-api/tutorials/february-2026-migration-guide)).

**Prerequisite: add an Artist field to each song.** Catalog songs only have a title today, and a title alone won't find the right track on Spotify. Each song needs an artist (the original artist for covers) before matching can work. Existing songs will need the artist filled in.

**How it would work**

1. User taps "Connect Spotify" and signs in (OAuth with PKCE; scopes to modify playlists).
2. Each catalog song gets matched to a Spotify track once, by title + artist, and the track ID is saved on the song.
3. "Export to Spotify" creates a playlist named after the set list (e.g. venue + date) and adds the matched tracks in order.
4. Songs with no match are listed so the user can pick the right version by hand.

**Catches to know about**

- Since February 2026, Development Mode apps need the app owner to have Spotify Premium, and only a small allowlist of Spotify users can sign in ([Spotify blog](https://developer.spotify.com/blog/2026-02-06-update-on-developer-access-and-platform-security)). That is fine for the band; opening it to the public needs Spotify's extended-access approval, which is a high bar.
- Some developers report 403 errors creating playlists in Development Mode after the 2026 changes ([community thread](https://community.spotify.com/t5/Spotify-for-Developers/Web-API-playlist-creation-returns-403-in-Development-Mode-no/td-p/7482480)). Worth a quick test before building much.
- Covers and originals share titles, so the match step should let the user confirm the right recording.

## Idea 2: Backing tracks in the catalog, played from Stage Mode

Each catalog song can carry an optional backing track (MP3 or WAV). Stage Mode then becomes a cue station: the drummer runs it on an iPad, and as the set moves to each song, he sees the lyrics and can start that song's backing track right there.

**How it would work**

1. On a song's catalog page, upload an MP3 or WAV as its backing track (optional; most songs won't have one).
2. In Stage Mode, the current song shows its lyrics plus a Play / Stop control when a backing track exists.
3. Advancing to the next song in the set list loads the next song's lyrics and track, ready to go.
4. Songs without a track show lyrics only, with no play control.

**Things to plan for**

- Offline at gigs: venue Wi-Fi is unreliable, so Stage Mode should download every track in the set to the iPad before the show.
- File size: WAV runs about 10 MB per minute, so a set with several tracks can reach a few hundred MB. Allow MP3, or convert on upload.
- Starting a track has to be instant and reliable: one big tap target, no accidental double-taps, and no lag between tap and sound.
- Audio routing: the iPad's output would feed the PA or the drummer's in-ears. Splitting a click track and the backing track into separate outputs is a possible later step.

**Open question:** should anyone besides the drummer be able to start tracks, or is it one device in control?
