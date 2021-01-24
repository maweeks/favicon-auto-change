# favicon-auto-change

## Prerequisites

- install inkscape
- `brew install imagemagick`
- `alias inkscape="/Applications/Inkscape.app/Contents/MacOS/inkscape"`

## Steps

- Create `icon.svg`
- Add dark style to svg if not already there, e.g.

  ```css
  path {
   fill: #0000ff;
  }
  @media (prefers-color-scheme: dark) {
   path {
    fill: #33ff33;
   }
  }
  ```

- Generate other files

  ```bash
  inkscape ./icon.svg --export-width=512 --export-filename="./icon-512.png"
  inkscape ./icon.svg --export-width=192 --export-filename="./icon-192.png"
  inkscape ./icon.svg --export-width=180 --export-filename="./apple.png"
  inkscape ./icon.svg --export-width=32 --export-filename="./tmp.png"
  convert ./tmp.png ./favicon.ico
  rm ./tmp.png
  ```

  If separate favicon needed for 16x16 use below

  ```bash
  inkscape ./icon.svg --export-width=32 --export-filename="./icon32.png"
  inkscape ./icon2.svg --export-width=16 --export-filename="./icon16.png"
  convert ./icon32.png ./icon16.png ./favicon.ico
  rm ./icon16.png
  rm ./icon32.png
  ```

## Links

Example [here](https://maweeks.github.io/favicon-auto-change/)

[Source](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs)
