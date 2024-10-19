# Compile Card Database

_This repo wouldn't be possible without Ryan Scherr's work on [Compile database](https://ryanascherr.github.io/compile/)_


## Purpose

This repo contains a JSON file and simple UI for viewing all the cards available in [Greater Than Game's Compile](https://greaterthangames.com/product-category/compile/) designed by [Michael Yang](https://boardgamegeek.com/boardgamedesigner/158096/michael-yang).

Please feel free to fork and contribute!!!


## Contents

This list will be updated as items are added/removed from the repo.

* cards.json  : This a JSON representation of all currently available cards.
* index.html  : A simple UI for viewing and filtering cards.
* style.css   : Style sheet used by index.html
* favicon.ico : Currently, a really boring cube. Looking for better options. :grinning:


## Using the UI

The UI defaults to displaying all cards, grouped by Protocol. In the lower right corner is an edit icon that, when clicked, will allow the user to group/un-group the files. In the upper right corner are two options:

* Filter Cards: Opens a modal that allows the user to select one or more options to filter the cards by:
    * Protocol
    * Value
    * Keyword
    * Set
* Clear Filters: Clicking this will clear all filters and reset the display to the default.

## Using Bookmarks and Query Parameters

The UI will update the URL as filters are selected/deselected to allow the user to bookmark and/or share a filter configuration.
You may also use named parameters in the query string like this:

    [https://chuckplayer.github.io/compile/?protocol=apathy&protocol=darkness&protocol=death&groupByProtocol=false](https://chuckplayer.github.io/compile/?protocol=apathy&protocol=darkness&protocol=death&groupByProtocol=false)

The UI will automatically convert this to use the "state" parameter to simplify the URL. The parameters it will accept are:

* protocol
* value
* keyword
* set

The values that may be passed for each parameter must match an associated value found in the cards.json file. Unrecognized filter parameters will be ignored.

**Example** This URL [https://chuckplayer.github.io/compile/?protocol=foobar&protocol=apathy](https://chuckplayer.github.io/compile/?protocol=foobar&protocol=apathy) will only display cards found in the Apathy protocol. The value "foobar" will be ignored.

## Example Card 

This is an example of one card that can be found in cards.json.

```json
    {
        "protocol": "Apathy",
        "value": 2,
        "top": {
            "emphasis": "",
            "text": "Ignore all middle commands of cards in this line."
        },
        "middle": {
            "emphasis": "",
            "text": ""
        },
        "bottom": {
            "emphasis": "When this card would be covered:",
            "text": "First, flip this card."
        },
        "keywords": {
            "flip": true
        },
        "set": "AX01"
    }
```

The properties for each card are:

* protocol  : The protocol the card is a member of.
* value     : The value of the card used in scoring.
* top       : The top command.
* middle    : The middle command.
* bottom    : The bottom command.
* keywords  : The keywords collection represents important actions relevant to the card, e.g., Give, Play, Rearrange, Refresh, etc.
* set       : The set that the card may be found in, e.g., MN01, AX01.

Top, middle, and bottom each have the following properties:

* emphasis  : Text on the card that deserves special emphasis for a given command, e.g., Start, End.
* text      : The remaining text for that command section.

