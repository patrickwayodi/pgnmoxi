Pgnmoxi
=======


Pgnmoxi converts chess game PGN files to other formats. Pgnmoxi is written in Python and
JavaScript using Jinja and jQuery.


## Overview

* Pgnmoxi takes a PGN chess file and converts it to these formats:
    - Web Page:
        * HTML
        * JavaScript
    - Video:
        * MP4
        * WebM
    - Image:
        * GIF
        * PNG
        * SVG
    - Data:
        * JSON
        * XML
    - Printing:
        * PDF

* Pgnmoxi has these main components:
    - Converting PGN to text based formats:
        * pgn2json.py, pgn2html.py, pgn2xml.py, pgn2svg.py
    - Converting PGN to binary formats:
        * pgn2gif.py, pgn2video.py, pgn2png.py, pgn2pdf.py
    - Creating lists and indexes:
        * collection.py, tournament.py
    - Generating a website:
        * generate_website.py
    - Settings and configuration:
        * settings.py
    - Templates:
        * src/templates
        * src/templates/game/.../index.html

* Pgnmoxi has these dependencies:
    - [Python Chess](https://pypi.org/project/chess)
    - Jinja
    - jQuery
    - Reportlab
    - [pgn2gif](https://github.com/dn1z/pgn2gif)


## Example Input

'''
[Event "Example Chess Championship"]
[Date "2023.05.19"]
[White "Jane Doe"]
[Black "Richard Roe"]
[Result "1-0"]

1. e4 e5 2. Nf3 Nc6 3. Bb5 a6 {This opening is called the Ruy Lopez.}
4. Ba4 Nf6 5. O-O Be7 6. Re1 1-0
'''


## Example Output for a Single Game

'''javascript
{
    "event": "Example Chess Championship",
    "date":"2023.05.19",
    "white":"Jane Doe",
    "black":"Richard Roe",
    "result":"1-0",
    "moves":"1. e4 e5 2. Nf3 Nc6 3. Bb5 a6 4. Ba4 Nf6 5. O-O Be7 6. Re1",
    "plies”:[“e4","e5","Nf3","Nc6","Bb5","a6","Ba4","Nf6","Be7","Re1"]
}
'''


## Example Output for Multiple Games

'''javascript
[
    {
        "pk": 1,
        "fields": {
            "white": "Jane Doe",
            "black": "John Doe",
            "plies": [
              {
                "ply": "d4",
                "eval": "0.33"
              },
              {
                "ply": "Nf6",
                "eval": "0.32"
              }
            ]
        }
    },
    {
        "pk": 2,
        "fields": {
            "white": "Richard Roe",
            "black": "Jane Doe",
            "plies": [
              {
                "ply": "d4",
                "eval": "0.33"
              },
              {
                "ply": "Nf6",
                "eval": "0.32"
              }
            ]
        }
    }
]
'''


## Adjustable Limits

* The default configutation has these adjustable limits in "settings.py":
    - Processing of a maximum of 5 plies (2.5 moves) per game
    - Processing of a maximum of 30 games per PGN file
    - 2 MB per uploaded file
    - Only 6 fields are processed: White, Black, Event, Date, Result, Moves
    - 7 milliseconds pause during each operation
    - 4 GB total storage space for all uploaded files

* The purpose of the limits is to prevent the program from running amock.


## Copyright and License

Pgnmoxi is free software: you can redistribute it and/or modify it under the terms
of the [GNU General Public License](https://github.com/patrickwayodi/pgnmoxi/blob/main/LICENSE)
license as published by the Free Software Foundation, either version 3 of the License,
or (at your option) any later version.

Pgnmoxi is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY;
without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
Pgnmoxi.

