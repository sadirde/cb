# cb - clean bookmarks

When you export your bookmarks from the bookmark manager (Library) in Firefox, you get an automatically generated HTML file. However, for whatever reason the `a` tags contain an `ICON` attribute with the base64 encoded data URI scheme of the favicon of the respective page. Because the URIs are so long, it inflates the size of the HTML file extremely, especially if you have many bookmarks. As an example: my 84.3 KB file is blown up to 3.8 MB!

To remedy this, I wrote a small shell script... ok, it's more of a sed one-liner.

All it takes is to download the script and to set the path where you always store your bookmark file in the first line.

```sh
file="path/to/bookmarks_file.html"
```

After that just copy the file to /usr/local/bin:

```
$ sudo cp cb /usr/local/bin
```

Optionally, you can also give the script the path to the file as the first argument; then the `file` variable is ignored. So these are the two ways to call it:

```
$ cb
$ cb path/to/my/bookmarks.html
```

The script then deletes all `ICON` attributes and the file reaches a normal size.