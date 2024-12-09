can 

# Plex-Get-DB-Media-Posters

A Linux Python script to download the poster images stored in your Plex media server database and save them as `poster.jpg` files in your movie and TV show library folders. The script assumes that each movie or TV show resides in its own folder.

## Features
- Downloads movie and TV show posters directly from your Plex server.
- Saves posters as `poster.jpg` in the corresponding media directories.
- Supports overwriting existing posters if desired.
- Configurable paths for both movies and TV shows.
- Works with Plex servers running in Docker or directly on a host system.

## Requirements
- Python 3.6 or greater.
- `requests` library for API communication.
- Linux or similar environment (the script can be adapted for Windows if needed).

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/CTinMich/Plex-Get-DB-Media-Posters.git
   ```
2. Navigate to the repository directory:
   ```bash
   cd Plex-Get-DB-Media-Posters
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
1. Open the script `Plex-Get-DB-Media-Posters.py` in a text editor or IDE.
2. Update the following configuration variables with your Plex server details:
   - `PLEX_URL`: Base URL of your Plex server (e.g., `http://192.168.1.100:32400`).
   - `PLEX_TOKEN`: Your Plex API token.
   - `MOVIES_SECTION_ID`: The library section ID for movies.
   - `TV_SECTION_ID`: The library section ID for TV shows.
   - `MOVIES_PATH_PREFIX_REAL`: Full path to your movie folders.
   - `TV_SHOWS_PATH_PREFIX_REAL`: Full path to your TV show folders.

3. Run the script with one or more options:
   - Copy movie posters:
     ```bash
     python3 Plex-Get-DB-Media-Posters.py -m
     ```
   - Copy TV show posters:
     ```bash
     python3 Plex-Get-DB-Media-Posters.py -t
     ```
   - Overwrite existing posters:
     ```bash
     python3 Plex-Get-DB-Media-Posters.py -m -t -o
     ```

4. The posters will be saved as `poster.jpg` in the respective media directories.

## Notes
1. **Docker Path Mapping**:
   - If you run Plex in a Docker container, configure `MOVIES_PATH_PREFIX_REAL` and `TV_SHOWS_PATH_PREFIX_REAL` to account for the difference between the Docker container path and the actual file path on your host system.

2. **TV Show Folder Matching**:
   - The script assumes that TV show folders follow the naming convention `{TV SHOW} {tvdb-xxxx}` for accurate matching.

3. **Getting Your Plex Token**:
   - Navigate to a movie in your Plex library, click **Get Info**, and then **View XML**. The token is in the URL under the `Plex-Token` parameter.

## Example Folder Structures
- Movies:
  ```plaintext
  /home/pi/Media/Movies/{MOVIE_NAME} {tmdb-xxxxx}/poster.jpg
  ```
- TV Shows:
  ```plaintext
  /home/pi/Media/TV Shows/{TV_SHOW_NAME} {tvdb-xxxx}/{SEASON}/poster.jpg
  ```

## Contributing
Feel free to fork this repository and submit pull requests. Bug reports and feature requests are welcome!

## License
This project is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License](LICENSE).

---
