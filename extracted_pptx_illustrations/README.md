# Extracted PowerPoint illustrations and media

Structure:

- `manifest.csv`: searchable index of every extracted file, including source deck and slide number when available.
- `<deck>/by_slide/slide_###/`: media files referenced directly by that slide.
- `<deck>/all_media_original_names/`: all media embedded in that PowerPoint with the original internal filenames.
- `<deck>/unassigned_media/`: embedded media not directly referenced by a normal slide, often theme/master/layout assets or other package media.

Note: PowerPoint vector shapes drawn directly on slides are stored as slide XML, not as standalone picture files, so they are not extracted as separate images here.
