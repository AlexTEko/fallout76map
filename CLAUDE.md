# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Fallout 76 map viewer project that uses OpenSeadragon to display a large map image as zoomable tiles. The project consists of:

- `map.png`: The source high-resolution Fallout 76 map image (approximately 194MB)
- `viewer.html`: An HTML page that uses OpenSeadragon to display the map with zoom/pan functionality

## Architecture

The viewer uses OpenSeadragon, a JavaScript library for displaying high-resolution zoomable images. It expects a Deep Zoom Image (DZI) format tile pyramid at `map_tiles.dzi`, which needs to be generated from the source `map.png` file.

## Development Tasks

### Generate Map Tiles
To make the map viewable, you need to generate a DZI tile pyramid from the source image. This can be done using:
- **vips**: `vips dzsave map.png map_tiles`
- **ImageMagick with dzi script**: Various scripts available for converting to DZI format
- **Python with pyvips or deepzoom.py**: Programmatic tile generation

### Local Development
Since the viewer loads OpenSeadragon from CDN, you can simply open `viewer.html` directly in a browser once tiles are generated. For proper testing with tile loading, serve the files locally:
- Python 3: `python3 -m http.server`
- Python 2: `python -m SimpleHTTPServer`
- Node.js: `npx http-server`

## Important Notes

- The `map_tiles.dzi` file and corresponding `map_tiles_files/` directory are not present and need to be generated before the viewer will work
- The viewer expects tiles to be in the same directory as the HTML file
- OpenSeadragon is loaded from CDN (unpkg), so internet connection is required