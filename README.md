# Google photos takeout metadata merging into their images

Match image metadata exported from Google Photos [Takeout](https://takeout.google.com/) back into your images.

Takes a folder, collects all `.json` files containing the metadata of the image, converts the image to `.jpg` and apply the metadata to it.

This is a Python3 command line tool for Linux, Mac and Windows,
based on [GooglePhotosMatcher](https://github.com/anderbggo/GooglePhotosMatcher) and [google-metadata-matcher](https://github.com/Greegko/google-metadata-matcher)


## Preparation

Note that `.heic`, `.png`, and even `jpeg` or `.JPG` will be converted to `.jpg`.
You might want to rename some files beforehand with the `rename` bash command, e.g.,
```shell
rename 's/\.JPG$/.jpg/' *.JPG
```

Don't forget the `.json` files too.


## Usage

Clone this repo and enter the folder
```shell
git clone https://github.com/pablogila/google-metadata-matcher
cd google-metadata-matcher
```

As always, it is recommended to run your project in a virtual environment:
```shell
python3 -m venv .venv
source .venv/bin/activate
```

Install the requirements with
```shell
pip3 install -r requirements.txt
```

You can now run the script with
```shell
merge_metadata.py [-h] [-w EDITED_WORD] [-o OPTIMIZE] [-m MAX_DIMENSION] source_folder output_folder

positional arguments:
  source_folder
  output_folder

optional arguments:
  -h, --help            show this help message and exit
  -w EDITED_WORD, --edited_word EDITED_WORD
                        Google Photos 'edited' word translation
  -o OPTIMIZE, --optimize OPTIMIZE
                        Optimalize the images (0 to 100), recommended: 75 (default: disabled)
  -m MAX_DIMENSION, --max_dimension MAX_DIMENSION
                        Resize the image restricting the max width,height dimension
```

For most cases, you can go with 75-80% JPG compression:
```shell
python3 src/merge_metadata.py source_folder output_folder -o 80
```


## Features

- Keeps Geo cordinates
- Keeps creation time
- Recursive folders image merging
- PNG, HEIC Support
- Resize option
- Optimalization option


## Main Dependencies

- Pillow - Image Editor lib
- pillow-heif - Image Editor lib HEIC (Apple) support
- piexif - Adjust Metadata for image

