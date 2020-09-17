# svg-to-iconfont

I needed to take a bunch of SVGs of different sizes and make webfont with CSS classes (like font awesome or icofont) out of them.

I was not happy with existing solutions, so I made my own.

## How to use

Make directory `font`, make  subdirectory `font/vectors`, put there the SVGs.

Go to folder `font`.

Run

```
docker run --user="$(id -u):$(id -g)" -v ${PWD}:/project karel3d/svg-to-iconfont icon-font-name
```

with icon-font-name being your icon font name.

Ignore the errors inkscape prints.

## Credits

The docker uses [fontcustom](https://github.com/FontCustom/fontcustom) (that uses [fontforge](https://github.com/fontforge/fontforge) under the hood)

The docker also uses [inkscape](https://gitlab.com/inkscape/inkscape) for resizing the SVGs, with script based on [this script](https://github.com/skagedal/svgclip) updated for python3

## how to use custom fontcustom config?

Add config.yml in the `font` folder, do

```
docker run --user="$(id -u):$(id -g)" -v ${PWD}:/project karel3d/svg-to-iconfont icon-font-name -c config.yml
```

## why not just use fontcustom?

Fontcustom is hard to install on its own and doesn't resize the SVGs automatically. Plus, all other existing docker fontcustom versions use ancient fontcustom version, so I use updated one.

This uses fontcustom under the hood though!

## why not just use webfont-generator?

[webfonts-generator](https://www.npmjs.com/package/webfonts-generator) is good and easy to install (just node), but it does not resize the underlying SVGs.

The underlying npm package, that actually does the job - [svgicons2svgfont](https://www.npmjs.com/package/svgicons2svgfont) - has some options for resizing and centering, but webfonts-generator doesn't use that, and there is a web of dead dependencies webfonts-generator is using - like [webfonts-generator](https://github.com/sunflowerdeath/webfonts-generator) that is dead for 4 years and is depending on some vulnerable dependencies. I didn't have a mood to dig into dead node packages.

## why is this so complex?

It uses inkscape and python3 for just resizing and centering SVGs, because I didn't find anything better that actually works.

It uses fontcustom because it works the best and is actually updated.

It uses fontforge because that's what fontcustom uses.

It uses ruby because fontcustom installs through rubygems.

## License

MIT
