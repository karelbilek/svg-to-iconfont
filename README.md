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

