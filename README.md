# HTTP API for [UnnaturalCode][]

# Install

    pip install -r requirements.txt
    pip install -e <fully-qualified-path-to-unnaturalcod>

Though you'll probably want to create a `virtualenv` before this.

# Run

    python server.py

# All rooted on resource `/{corpus}`

 * Currently, only the `py` corpus is supported. Obviously, `py` is the
   occam-π corpus.


# `GET /{corpus}/`—Corpus info

Returns metadata for the given corpus. Metadata includes:

 * `fullname`
 * `last_updated`
 * `description`
 * `language`—programming or otherwise
 * `order`
 * `smoothing`—Probably always `ModKN`
 * `vocabulary`
   * `size`
   * `categories`—lists syntactic categories



# `GET /{corpus}/predict/{context*}`—Predict

     GET /py/predict/<unk>/for/i/in HTTP/1.1

     {"suggestions": [3.45, ["range", "(", "5", ")", ":"]]}

## Mandatory arguments

Must give context as a context path.

### `{context*}`

Preceding token context. The more tokens provided, the better. See
[Context format](#context-format).



# `POST /{corpus}/xentropy`—calculate cross entropy

## Mandatory arguments

`?f` for an entire file.



# `POST /{corpus}/`

Trains the corpus with some tokens from a specific source.

## Mandatory arguments

### `?f`

A plain-text file that will be tokenized and trained upon.



# Context Format

## Formal Grammar

    token-list  = token
                / token "/" token-list

    token       = [ syncat ":" ] chars

    chars       = { ~all characters other than ":"~ }
    syncat      = [ ~all characters other than "/" and ":"~ ]

# Licensing

Like [UnnaturalCode][], UnnaturalREST is licensed under the AGPL3+.

© 2014 Eddie Antonio Santos

UnnaturalREST is free software: you can redistribute it and/or modify it
under the terms of the GNU Affero General Public License as published by
the Free Software Foundation, either version 3 of the License, or (at
your option) any later version.

UnnaturalREST is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero
General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with UnnaturalREST. If not, see http://www.gnu.org/licenses/.

[UnnaturalCode]: https://github.com/orezpraw/unnaturalcode
