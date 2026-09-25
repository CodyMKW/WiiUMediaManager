# Wii U Media Manager

A fast, lightweight, and completely local browser tool to view, sort, and manage screenshots and video clips from your Wii U SD card. 

Instead of manually digging through obscure folder structures, this tool automatically scans your SD card for Wii U media and presents it in a clean, dark-mode gallery. Everything runs **100% locally in your browser**—no files are ever uploaded to any server.

## ✨ Features

* **Zero Install & Local:** It's just a single HTML file. Open it in Chrome, Edge, or Firefox, and it works instantly.
* **Auto-Discovery:** Automatically hunts down images and videos inside `wiiu/screenshots`, `wiiu/screencaptures`, and `DCIM` directories.
* **Custom AVI Thumbnail Extractor:** Modern browsers often fail to generate thumbnails for the Wii U's native Motion JPEG (MJPEG) `.avi` video clips. This tool includes a custom binary parser that reads the raw file bytes to extract the first JPEG frame, guaranteeing thumbnails for all your clips.
* **Favorites System:** Star your best Splatoon matches or Smash Bros. moments. Favorites are saved to your browser's local storage so they remain starred the next time you plug in your SD card.
* **Built-in Lightbox:** View full-resolution images and download your favorites directly from the web interface.

## 🚀 How to Use

1. Download the `index.html` file.
2. Double-click `index.html` to open it in your web browser.
3. Plug your Wii U SD card into your computer.
4. Click **Open SD card** in the web interface.
5. When the file picker opens, select the **root directory** of your SD card and grant the browser permission to view the files.
6. Browse, star, and download your media!

## 🛠️ Technical Details

* **Tech Stack:** Vanilla HTML, CSS, and JavaScript. No external dependencies, libraries, or frameworks.
* **Permissions:** The tool uses the HTML5 `<input type="file" webkitdirectory>` API. This grants the browser temporary, read-only access to scan the selected folder for media. 
* **AVI Playback Note:** While the tool successfully extracts thumbnails for AVI files, not all modern browsers support playing MJPEG AVIs natively in the `<video>` tag. You can still download the AVIs directly from the Lightbox to play them in software like VLC.

## 📝 License

MIT License. Feel free to fork, modify, and host on your own setup.