# Obsidian Plugin "Table to CSV Exporter"

This is my very first attempt in writing a plugin for [Obsidian](https://obsidian.md).

## What does it do?

The purpose of this plugin is to be able to export table data from a pane in reading mode into a CSV file.

Background: The fabulous Dataview plugin for Obsidian allows to dynamically create tables from an SQL-like query over your notes' metadata.
I wanted to be able to further use this created data in external applications, like MS Power BI, to create visualizations of that data.
But the plugin can export any table into a CSV file, even those you "hard-coded" in Markdown (if that makes sense for you) or those that were created by some other plugin.

## Installation

As long as my plugin isn't officially added to the list of community plugins inside Obsidian itself you can install it manually in a few easy steps:

1. Go into the `.obsidian` sub folder inside of your vault folder. An easy way is to click on the little folder icon on the Community plugins settings page.
![](img/install-1.png)
2. Create a new folder inside the `plugins` folder (you can name it however you want but maybe `table-csv-export` or sim. makes sense).
3. Copy the two files `main.js` and `manifest.json` from the [release](https://github.com/metawops/obsidian-table-to-csv-export/releases) you downloaded into that folder.
4. In Obsidian, click on the little reload icon in the Community plugins settings:
![](img/install-2.png)
5. Scroll down and switch on the new plugin:
![](img/install-3.png)

That's it, you're all set. Find the plugin's settings under the "Plugin Options" sidebar of Obsidian's settings dialog:
![](img/install-4.png)

## Settings

My plugin allows you to configure a few things in its settings:

* **The base filename of the CSV file**

   This is the first part of the filename of the CSV file you're about to save.

   **Default**: `table-export`

* **A file number addition**

   This gets added to the base filename (after a hyphen). After this, the extension `.csv` is added.  
   This number gets incremented by one after each succesful export and resetted to 001 after reaching 999.  
   Normally you won't need to interfere with this in the settings but you can change it if you want.  
   **But be careful!** Don't mess with this. Don't change this to text or something different than numbers. And stay in the ### scheme (three ciphers max., leading zeroes).  
   It may become neccessary to either change this number manually or to delete/rename/move files out of your vault folder.  
   No worries, though: the plugin never overwrites any files and warns you if a file already exists.

   **Default**: `001`

* **The separation character**

   Here you can select the character that separates the data fields in the CSV file. The dropdown box contains the usual suspects like comma, semicolon and tab. But there are some unusual choices as well.

   **Default**: `;`

* **Quote data**

   If you want the data cells in the CSV file to be enclosed in quotation marks you can choose to do so here. In the dropdown box you can choose between either double quotation marks (`"`), single quotation marks (`'`) or not to quote data at all.

   **Default**: no quoting

* **Handling of CR/LF in data**

   In some rare cases you might have return (CR) or linefeed (LF) characters inside of data fields/cells. This will break the CSV file. With this setting you can select how you want to handle these characters. You can either simply strip them, replace them with a single space character or replace them with the fixed string `[CR]`so that you later can still see that there once _was_ some kind of return character in your data.

   **Default**: Replace all CR & LF characters with one space

* **Copy to clipboard, too**

   Optionally you can copy the CSV string to the clipboard, too.
   
   **Default**: `off`

## Usage

The plugin adds a new command: "Export table to CSV file". This will only work when your currently active pane is in reading mode. When the command is executed a `.csv` file is written according to the settings in your vault's main folder. This CSV file contains the data of the *first* table in the reading mode of the note.

The plugin works on mobile, too. (Tested on iPadOS only, though.)

## Current limitations

Of course, there's always room for improvement. **As of version 0.1.4, there are the following limitations/restrictions**:

* The plugin currently exports only the first table that it finds in the reading mode of a note.
* The plugin saves the CSV file directly into you vault's main folder. A feature to select another folder inside your vault will be added later.

## Thanks

I'd like to thank several people here. Without them this plugin wouldn't have come to live.

* [Edmund Gröpl](https://twitter.com/groepl) – for bringing up the problem at all and his encouragement over all the years.
* [Marcus Olsson](https://github.com/marcusolsson) – for starting the [Obsidian Plugin Developer Docs](https://marcus.se.net/obsidian-plugin-docs/) project which I highly recommended, especially for beginners. He's on Twitter, too: [@marcusolsson](https://twitter.com/marcusolsson)
* [Johannes Theiner](https://github.com/joethei) – a very kind and helpful user over at the official Obsidian Discord server. I met him in the `#plugin-dev` channel and his answers to my questions were very helpful. He's also on Twitter: [@joethei](https://twitter.com/joethei)

## Contact

Please leave feedback here in the GitHub discussions or file a new issue if you found a bug or have a feature request.
You can reach me via Twitter, too: [@metawops](https://twitter.com/metawops)

## Sponsoring

If this plugin adds value for you and you would like to help support continued development, please consider sponsoring this repository via [GitHub Sponsors](https://github.com/sponsors/metawops), [PayPal](https://paypal.me/stefanwolfrum) or [Buy me a coffee](https://www.buymeacoffee.com/metawops).

Made with ❤️ in Bonn, Germany.
