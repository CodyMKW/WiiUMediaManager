# Wii U Media Manager

A fast, lightweight browser tool to view, sort, and manage screenshots and video clips from your Wii U SD card, and optionally share them straight with a friend. 

Instead of manually digging through obscure folder structures, this tool automatically scans your SD card for Wii U media and presents it in a clean, dark-mode gallery. Your files are never uploaded to any server: browsing is 100% local, and if you choose to share with a friend, it goes directly from your browser to theirs.

## ✨ Features

* **Zero Install & Local:** It's just a single HTML file. Open it in Chrome, Edge, or Firefox, and it works instantly.
* **Auto-Discovery:** Automatically hunts down images and videos inside `wiiu/screenshots`, `wiiu/screencaptures`, `riftwii/screenshots`, and `DCIM` directories.
* **Real AVI Playback (with sound):** Browsers can't play the Wii U's native Motion JPEG (MJPEG) `.avi` clips, so this tool plays them itself. It reads the AVI's internal structure, decodes each frame, and draws them on a canvas at the clip's original frame rate, with the audio track pulled out and kept in sync. You get play/pause, a seek bar, and volume controls.
* **Custom AVI Thumbnail Extractor:** A custom binary parser reads the raw file bytes to extract the first JPEG frame, guaranteeing thumbnails for all your clips.
* **Peer-to-Peer Sharing:** Click **Connect with a friend**, copy your invite link, and send it over. When they open it, you connect automatically and each of you can browse the other's gallery in a separate tab. Thumbnails load as you scroll, and full files are fetched on demand with a progress percentage. You'll also see what your friend is currently viewing, and a heads-up if they go offline.
* **Favorites System:** Star your best Splatoon matches or Smash Bros. moments. Favorites are saved to your browser's local storage so they remain starred the next time you plug in your SD card.
* **Built-in Lightbox:** View full-resolution images, play videos, and download your favorites directly from the web interface.

## 🚀 How to Use

1. Download the `index.html` file.
2. Double-click `index.html` to open it in your web browser.
3. Plug your Wii U SD card into your computer.
4. Click **Open SD card** in the web interface.
5. When the file picker opens, select the **root directory** of your SD card and grant the browser permission to view the files.
6. Browse, star, play, and download your media!

## 🤝 Sharing With a Friend

1. Click **Connect with a friend** and set your name.
2. Click **Copy** on your invite link and send it to your friend.
3. They open it, you connect automatically, and a tab with their name appears next to Wii U and DCIM.

A few things worth knowing:

* **Both of you need the page open at the same time.** There's no server holding your files, so if either tab closes, the connection ends.
* **Invite links need the page to be hosted somewhere** (GitHub Pages works great). A link made from a file you opened from your own computer only works on your own computer. If you're not hosting it, your friend can instead paste your Peer ID into the "paste a friend's invite link / ID" box.
* **Your invite link is basically a key.** Anyone who has it can connect to you and browse what you've loaded.
* **You don't need your own SD card loaded** to browse a friend's gallery.

## 🛠️ Technical Details

* **Tech Stack:** Vanilla HTML, CSS, and JavaScript. The only external piece is [PeerJS](https://peerjs.com/) (loaded from a CDN), which is used purely for the optional friend-sharing feature. Everything else works offline.
* **Permissions:** The tool uses the HTML5 `<input type="file" webkitdirectory>` API. This grants the browser temporary, read-only access to scan the selected folder for media. 
* **AVI Playback:** The player walks the AVI's RIFF structure to find every MJPEG frame, then decodes only the frames it needs (plus a short lookahead) so even long clips start quickly. The audio is stored as raw PCM inside the AVI, so it's wrapped in a WAV header and used as the master clock to keep picture and sound locked together. AVIs that use a different codec fall back to a download-only message.
* **P2P:** Connections run over WebRTC via PeerJS. Your Peer ID is saved in your browser so your invite link stays the same between visits. Files move in 64 KB chunks between the two browsers; nothing passes through a server except the initial handshake.

## 📝 License

MIT License. Feel free to fork, modify, and host on your own setup.
