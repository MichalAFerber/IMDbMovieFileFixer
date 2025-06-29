![IMDbMovieFileFixer](IMDbMovieFileFixer.png)

# IMDbMovieFileFixer

IMDbMovieFileFixer is a Python script designed to streamline and enhance your movie file organization. This tool automatically renames movie files in a specified folder to a standardized format, corrects common grammar mistakes, and verifies movie titles against official names on IMDb. Unlike similar tools like movie-file-fixer or imdb-rename, it emphasizes grammar correction and detailed logging for transparency, making it ideal for movie enthusiasts and collectors.

## Features

- **Standardized Renaming**: Renames movie files to a consistent format including the release year (e.g., "Movie Title (2023).mp4").
- **Grammar Correction**: Fixes common grammar mistakes in movie titles (e.g., "Dont" to "Don't").
- **Cleanup**: Removes unnecessary information (e.g., resolution, codec) from filenames.
- **IMDb Verification**: Cross-checks titles with IMDb and logs discrepancies.
- **Duplicate Handling**: Appends an index to duplicate filenames (e.g., "Movie (2023) [1].mp4").
- **Detailed Logging**: Generates a log file detailing all changes, discrepancies, and errors.

## Installation

### Prerequisites

- **Python 3.6 or higher**: Download from python.org if not installed. Check your version with `python --version`.
- **Git**: Required to clone the repository. Install from git-scm.com if needed.

### Setup Virtual Environment (Recommended)

To avoid dependency conflicts, use a virtual environment:

1. Create a virtual environment:

   ```bash
   python -m venv env
   ```

2. Activate it:

- **Windows**: `env\Scripts\activate`
- **Unix/Linux/Mac**: `source env/bin/activate`

### Install Required Libraries

Install the necessary Python libraries using `pip`:

```bash
pip install requests beautifulsoup4
```

### Clone the Repository

1. Clone the repository:

    ```bash
    git clone https://github.com/MichalAFerber/IMDbMovieFileFixer.git
    ```

2. Navigate to the project directory:

    ```bash
    cd IMDbMovieFileFixer
    ```

Alternatively, download the script directly from the GitHub repository.

## Usage

1. **Set the Folder Path**: Open `IMDbMovieFileFixer.py` in a text editor and set the `folder_path` to your movie directory:
   
    ```python
    folder_path = "/path/to/your/movie/folder"
    ```

2. **Run the Script**: In the terminal, navigate to the project directory and execute:

    ```bash
    python IMDBMovieFileFixer.py
    ```
    
3. Review the Log File: Check the generated log file (e.g., `_output 2024-12-23 23-40-15.txt`) in the project directory for details on changes and discrepancies.

**Note**: Back up your movie files before running the script to prevent accidental data loss. For large collections, process in smaller batches to avoid IMDb rate limits.

## Configuration Options

Customize the script by modifying `IMDbMovieFileFixer.py`:

- **Renaming Format**: Adjust the `rename_format` variable to change the output format (default: "{title} ({year}).{ext}").
- **Grammar Rules**: Edit the `correct_grammar` function to add or remove grammar corrections (e.g., change "Dont" to "Don't" or add new patterns).
- **IMDb Request Delay**: Modify `time.sleep(1)` to increase the delay between IMDb requests (e.g., `time.sleep(2)` for rate limit issues).

## Output File

The script generates a log file in the project directory, named with the current date and time (e.g., `_output 2024-12-23 23-40-15.txt`). It includes:

- Renamed files and their new names.
- Duplicate filenames and how they were handled.
- Official IMDb names and any discrepancies.
- Errors encountered during processing.

## Example

### Before:

```bash
Millers.2013.1080p.BluRay.x264.YIFY.mp4
Dont.Breathe.2016.720p.WEBRip.x264.AAC-ETRG.mkv
```

### After:

```bash
Miller's (2013).mp4
Don't Breathe (2016).mkv
```

## Supported File Types

The script processes common video file extensions: `.mp4`, `.mkv`, `.avi`, `.mov`, `.wmv`. Other file types in the folder are ignored.

## Troubleshooting

### Installation Issues

- Python Version Error: Ensure Python 3.6+ is installed (`python --version`).
- Missing Libraries: Run `pip install requests beautifulsoup4` to install dependencies.

### Runtime Errors

- Folder Path Issues: Verify the `folder_path` exists and you have read/write permissions.
- File Not Found: Ensure files aren’t being moved or deleted during script execution.
- Permission Denied: Run the script with elevated privileges (e.g., `sudo python IMDbMovieFileFixer.py` on Unix).

### IMDb Connection Problems

- Rate Limiting: Increase the delay in `time.sleep(1)` to `time.sleep(2)` or higher.
- Search Issues: Check your internet connection and IMDb accessibility. Update the `search_imdb` function’s URL or headers if IMDb’s structure changes.
- Multiple Results: The script uses the first IMDb result. Enhance the `search_imdb` function for better filtering if needed.

### Other Issues

- Incorrect Filename Format: Ensure filenames include the movie name and year. Adjust the regex in the script for custom formats.
- Encoding Issues: Use UTF-8 encoding for files (e.g., `open(filename, 'r', encoding='utf-8')`).
- Special Characters: The script handles most special characters, but add custom handling in the renaming logic if issues arise.

## FAQ

### General Questions

**Q: What happens if there’s a duplicate filename?**  
A: The script appends an index (e.g., "Movie (2023) [1].mp4") to ensure uniqueness".

**Q: Can I use this for TV shows or other media?**  
A: The script is designed for movies. TV show support requires modifications to handle episodic naming.

**Q: Does it support non-English movie titles?**  
A: Yes, but ensure IMDb has the title. Special characters are handled, but complex cases may need custom logic.

**Q: What file formats are supported?**
A: Supports `.mp4`, `.mkv`, `.avi`, `.mov`, `.wmv`. Contact the maintainer for additional formats.

### Customization

**Q: Can I customize the renaming format?**  
A: Yes, modify `rename_format` in the script (e.g., "{title} [{year}]").

**Q: How do I change the delay between IMDb requests?**  
A: Adjust `time.sleep(1)` in the script to a higher value (e.g., `time.sleep(2)`).

### Technical Issues

**Q: What if IMDb’s website changes?**  
A: Update the `search_imdb` function’s BeautifulSoup selectors to match IMDb’s new structure.

**Q: How do I preview changes before renaming?**  
A: If IMDb changes its website structure, the script might need updates to the HTML parsing logic. Check the `search_imdb` function and adjust the BeautifulSoup selectors accordingly.

**Q: How do I revert changes?**  
A: Use the log file to manually rename files back. Automating reversion requires additional scripting.

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.
2. Follow PEP 8 coding standards.
3. Test changes locally with a sample movie folder.
4. Submit a pull request with a clear description of your changes.

For major changes, open an issue first to discuss with the maintainer.

## IMDb Data Usage

This tool uses IMDb data for title verification. Ensure compliance with IMDb’s Conditions of Use. Avoid excessive requests to prevent rate limiting.

## License
This project is licensed under the GNU General Public License v3.0. See the LICENSE file for details.

## Acknowledgements
- [BeautifulSoup Documentation](https://tedboy.github.io/bs4_doc/)
- [IMDb](https://www.imdb.com/)
- [Plex Media Server]([https://plex.tv](https://www.plex.tv/media-server-downloads/) 
- [Python Requests Library](https://pypi.org/project/requests/)

## Contact
For support or questions, contact the maintainer via GitHub Issues.
