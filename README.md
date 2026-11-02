# HTV IPTV playlist

Public M3U playlist for HTV on Xiaomi Android TV.

## Fixed playlist URL

`https://raw.githubusercontent.com/dohuubach/htv-iptv-playlist/main/HTV-Combined-VN-Sports-News-US.m3u`

Keep this file path and the `main` branch unchanged. The TV's HTV app can continue using the same URL after playlist updates.

## Daily automatic update

GitHub Actions workflow: [Update IPTV playlist](.github/workflows/update-playlist.yml)

- Runs every day at 01:23 UTC (08:23 Vietnam time, UTC+7).
- Can also be started manually from the repository's Actions tab using "Update IPTV playlist" → "Run workflow".
- Downloads the Vietnam, Sports, News, and USA M3U source lists from iptv-org.
- Checks that all four inputs are valid M3U files and that each source and the combined playlist meet minimum channel-count thresholds.
- Skips incomplete records, groups channels by source, and validates that each output channel has a stream URL.
- Commits only the existing playlist file when its content changes. The file name, branch, and raw URL remain unchanged.
- If a download or validation fails, the workflow stops without replacing the last known-good playlist.

## Notes

The playlist is a directory of public stream addresses, not a guarantee that every stream is available in every region or remains online. Source providers can remove, move, or restrict streams. GitHub's scheduled workflow can run later than its requested time; use manual workflow dispatch when an immediate refresh is needed.
