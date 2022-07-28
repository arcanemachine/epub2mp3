# epub2mp3

Convert an ePub to an mp3 using Microsoft's excellent Edge TTS (text-to-speech) service.

#### Requires Linux to run the BASH scripts. The parent repos may work with Windows. I haven't checked.


## About

This is a repo I've thrown together that consists mainly of other people's work. All I've done is put everything in a single place to make it easier for myself (and you?) to use.

Credit to those who did the actual work:
  - [epub2txt](https://github.com/ffreemt/epub2txt): Convert `epub` to `txt` (License: MIT)
  - [edge-tts](https://github.com/rany2/edge-tts): TTS module for `txt` to `mp3` conversion (License: GPL 3.0)

**Because of the GPL 3.0 licensing used in `edge-tts`, this repo is also GPL 3.0 licensed.**


## Instructions

Requires `git` (obviously) and `python3`.

1. Clone the repo (Requires `git`):
  - `git clone https://github.com/arcanemachine/epub2mp3`

3. Navigate to the directory that contains the new repo.
  - `cd epub2mp3`

5. (Optional but recommended) Create and activate a Python virtual environment:
  - `python3 -m venv venv`
  - `source venv/bin/activate`

6. Install the requirements:
  - `python3 -m pip install -r requirements.txt`

7. Convert your `epub` to an `mp3`:
  - `./epub2mp3 your-file.epub` (Output file will be `your-file.mp3` in the same directory)

## Notes

- If you examine `epub2mp3`, you'll see it's just a paper-thin wrapper for `epub2txt` and `edge-tts`.
  - If you aren't satisfied with the default options, please take a look at these repos to see what they can do for you.
  - You can customize `edge-tts` quite a bit depending on your needs (By comparison, `epub2txt` offers very little customization).

- The text-to-speech service seems to have a bit of trouble with some phrases, e.g. initials like 'John F. Kennedy' makes the TTS pause since it thinks it's at the end of a sentence. Therefore, you may want to convert to a `txt` file to process it before converting the `txt` file to an `mp3`:
  1. Convert the `epub` to a `txt` file:
    - `epub2txt -f your-file.epub`
      - Or use script in project root directory: `./epub2txt your-file.epub`
  2. Process the file as needed
  3. Convert the `txt` file to an `mp3`:
    - `./txt2mp3 your-file.txt` (Or use `edge-tts` directly)
