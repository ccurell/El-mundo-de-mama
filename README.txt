MUM'S WORLD - how to edit

WHAT'S WHERE
  index.html          the website. Edit the block "EDIT EVERYTHING IN THIS BLOCK" for titles,
                      settings (CONFIG) and the people/avatars (PEOPLE).
  data/places.geojson points  - homes and trips to a place
  data/areas.geojson  polygons - trips that covered a region (e.g. a tour of Andalucía)
  photos/  people/  videos/    your media files
  world.js            country outlines - don't touch

EDITING THE TRIPS IN QGIS
  1. Drag the two files in /data into QGIS (they're in EPSG:4326 / WGS84).
  2. Select a layer > Toggle Editing (pencil) > Add Point/Polygon feature.
     Draw it, then fill in the attribute form. Save Layer Edits - this writes straight
     back into the .geojson file, no exporting needed.
  3. You can also edit text in the Attribute Table (F6).

  Fields (the same in both files):
    name          place name
    type          lived  or  visited
    start         year it started (number), e.g. 2005
    end           year it ended. Empty = for homes: still lives there / for trips: same year
    with          who came, ids from PEOPLE in index.html separated by ;  e.g.  papa;clau
                  (empty = she went alone)
    story         the story
    photos        photo paths separated by ;  e.g.  photos/teide1.jpg;photos/teide2.jpg
    captions      optional captions, same order as photos, separated by ;
    video         an unlisted YouTube link, or videos/clip.mp4
    color         optional colour for an area, e.g. #4a90c2 (empty = default orange)

  Areas get a pin in their middle; clicking the pin or the shape opens the card.

  Tips
   - Simplify very detailed polygons (Vector > Geometry Tools > Simplify) so the site stays fast.
   - Making a brand-new layer instead? Export it as GeoJSON, CRS EPSG:4326, with the same
     field names, put it in /data and add its name to dataFiles in CONFIG (index.html).
   - Delete the example features (the 'demo:' photos) once you add real ones.

PHOTOS / AVATARS
  - Resize photos to ~1600px wide. Write them as photos/name.jpg in the photos field.
  - Real headshots: put them in /people and use  photo: 'people/papa.jpg'  in PEOPLE.

PUTTING IT ONLINE WITH GITHUB (free) - do this once
  1. Create a free account at github.com.
  2. Top-right "+" > New repository. Name it e.g. mums-world, choose Public, click Create repository.
     (Free GitHub Pages needs a public repository - anyone with the address could find it,
      so only share the link with family.)
  3. On the new repo page click "uploading an existing file". Open the mums-world folder on
     your computer, select EVERYTHING inside it (index.html, world.js, README.txt, .nojekyll and
     the data, photos, people, videos folders) and drag it in. Click "Commit changes".
     Tip: if .nojekyll is hidden on your computer, skip it - it's optional.
  4. Settings (tab at the top of the repo) > Pages (left menu) > Source: "Deploy from a branch",
     Branch: main, folder: / (root) > Save.
  5. Wait 1-2 minutes and refresh that page: it shows your address, something like
     https://YOUR-USERNAME.github.io/mums-world/   - that's the site to send to your mum.

EDITING ONCE IT'S ONLINE (no QGIS needed)
  Places and areas, on a map - geojson.io
   - Go to geojson.io, sign in with GitHub when it asks, and use its GitHub option to open
     your repo > data > places.geojson (or areas.geojson).
   - Click a pin/area to edit its fields, or use the point / polygon tools to add new ones
     (add the same fields: name, type, start, end, with, story, photos, captions, video, color).
   - Save back to GitHub. The live site updates within 1-2 minutes (refresh with Ctrl+F5).
   - If saving to GitHub gives you trouble: save/download the file from geojson.io (or QGIS),
     then on github.com open the data folder > Add file > Upload files > drop it in with the
     same name > Commit changes. It replaces the old one.
  Photos
   - On github.com open the photos folder > Add file > Upload files > drag photos in > Commit.
   - Then type them in the photos field, e.g. photos/teide1.jpg;photos/teide2.jpg
     (names are case-sensitive: Teide1.JPG is not teide1.jpg).
   - Shrink them to ~1600px wide first; GitHub rejects files over 25 MB through the website.
  Videos
   - Best as unlisted YouTube links in the video field - they play inside the card.
  Avatars, titles, settings
   - On github.com click index.html > the pencil icon (Edit) > change the PEOPLE / CONFIG
     block > Commit changes.

  Every change is saved in GitHub's history, so a mistake can always be undone
  (open the file > History).

PREVIEWING ON YOUR COMPUTER (optional)
  Browsers won't let a page read the /data files when you just double-click index.html.
  Double-click it and drag the .geojson files onto the map, or use VS Code's "Live Server".

SETTINGS ALREADY ON FOR THE ONLINE VERSION
  basemap: 'satellite'  - real satellite imagery (Sentinel-2 cloudless by EOX, free for
                          non-commercial use). If it ever fails to load, the drawn globe is used.
  embedVideos: true     - YouTube videos play inside the card.
