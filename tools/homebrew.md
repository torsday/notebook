# [Homebrew](http://brew.sh)

## Basics

### choose specific version of installed package

```bash
% brew info imagemagick
imagemagick: stable 6.9.0-3 (bottled), HEAD
http://www.imagemagick.org
/usr/local/Cellar/imagemagick/6.8.8-9 (1429 files, 21M)
/usr/local/Cellar/imagemagick/6.8.9-1 (1432 files, 22M)
/usr/local/Cellar/imagemagick/6.9.0-3 (1440 files, 22M) *
```

### set active version

```bash
% brew switch imagemagick 6.8.9-9
```

## Troubleshooting

```sh
brew doctor
```

### `/usr/local` is not writable.

```sh
sudo chown -R $USER:admin /usr/local/include
```
