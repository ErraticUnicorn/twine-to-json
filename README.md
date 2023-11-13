# Twine-to-JSON-to-Godot

A story format for converting a Twine 2 story to JSON with special support for Harlowe 3.x.

Twine-to-JSON is inspired by [Twison](https://github.com/lazerwalker/twison), which in turn was inspired by [Entweedle](http://www.maximumverbosity.net/twine/Entweedle/).


## Setup

From the Twine 2 homescreen, select `Formats` and then `Add a New Format`. At the prompt, paste in one of the addresses below:

For vanilla Twine-to-JSON (without special support for Harlowe 3.x), use this address:

```
https://erraticunicorn.com/twine-to-json-to-godot/dist/twine.js
```

## Export

Once you've installed format, enter your story and choose `Change Story Format`. Select the new format and return to your story. Selecting `Play` will export a JSON file.

From within your story, set the story format to Twison. Choosing "Play" will now give you a JSON file.


## Example Output

```json
{
  "name": "GeoTest",
  "creator": "Twine",
  "creatorVersion": "2.3.5",
  "schema": "Harlowe 3 to JSON",
  "schemaVersion": "0.0.5",
  "uuid": "A0472E68-7822-4211-9F11-5CBD919162DC",
  "passages": [
    {
      "name": "StoryStart",
      "tags": "",
      "id": "1",
      "text": "Once upon a time there was a sheep.\n[[Pet the sheep -> PetSheep]]",
      "links": [
        {
          "linkText": "Pet the sheep",
          "passageName": "PetSheep",
          "original": "[[Pet the sheep -> PetSheep]]"
        }
      ],
      "hooks": [],
      "cleanText": "Once upon a time there was a sheep."
    },
    {
      "name": " PetSheep",
      "tags": "",
      "id": "2",
      "text": "You pet the sheep. The end.",
      "links": [],
      "hooks": [],
      "cleanText": "You pet the sheep. The end."
    }
  ]
}
```


## Why use Twine-to-JSON instead of Twison (et al)?

You should probably use Twison. Twine-to-JSON currently has an unstable API and is less well tested. However, if Twison isn't working for you, you may have better luck with Twine-to-JSON. This project uses a more reliable method of detecting links and won't be fooled by embeded json arrays. It also detects some features specific to Harlowe.


## Contributing

Please do.

## Development

If you want to hack on the package itself:

1. Clone this repo and run `npm install` to install dependencies.
2. Make your changes to the unminified code in the `src` folder
3. Run `npm run build` to compile your source into a `format.js` file that Twine 2 can understand. It'll be placed in the `dist` folder. Alternatively, you can run `npm run watch` to watch the `src` directory for changes and auto-recompile every time you save.

### Testing your changes locally

Running `npm start` will start the `watch.js` auto-compile behavior, and also start a local web server that serves the compiled `format.js` file. By default, this will be available at `http://localhost:3000/format.js`. Add that URL as a story format to your copy of Twine 2; every time you save a source file and then re-generate the "Play" view of your story in Twine, it should use the latest version of your code.

This is easier to do with the browser-based version of Twine 2 than with the downloadable copy, as you can just refresh your output page and it'll use the latest version of Twison.
