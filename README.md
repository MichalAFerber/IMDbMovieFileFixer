![IMDbMovieFileFixer](IMDbMovieFileFixer.png)

# IMDbMovieFileFixer

IMDbMovieFileFixer is a Python script designed to streamline and enhance your movie file organization. This tool automatically renames movie files in a specified folder to match a standardized format, corrects common grammar mistakes, and verifies movie titles against the official names on IMDb. It logs all changes and discrepancies, ensuring your movie collection is neatly organized and accurately labeled.

## Features
- **Standardized Renaming**: Renames movie files to a consistent format including the release year.
- **Grammar Correction**: Corrects common grammar mistakes in movie titles.
- **Cleanup**: Removes unnecessary information (e.g., resolution, codec) from filenames.
- **IMDb Verification**: Checks and logs official movie names from IMDb.
- **Duplicate Handling**: Handles duplicate filenames by appending an index.
- **Detailed Logging**: Provides detailed logging of all changes and discrepancies.

## Installation

### Prerequisites
Ensure you have Python 3.6 or higher installed on your machine. You can download it from python.org.

### Required Libraries
Install the required Python libraries using `pip`:
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

## Usage
1. Define the folder path containing your movie files in the script:
    ```python
    folder_path = "/path/to/your/movie/folder"
    ```
2. Run the script:
    ```bash
    python IMDBMovieFileFixer.py
    ```
3. Review the log file for details on changes made and any discrepancies found.

## Output File
The script generates an output file that logs all changes and discrepancies. The output file is named with the current date and time, for example: `_output 2024-12-23 23-40-15.txt`. This file includes:
- Renamed files and their new names.
- Duplicate filenames and how they were handled.
- Official IMDb names found and any discrepancies with the filenames.
- Any errors encountered during the process.

## Example
Before:
```
Millers.2013.1080p.BluRay.x264.YIFY.mp4
Dont.Breathe.2016.720p.WEBRip.x264.AAC-ETRG.mkv
```
After:
```
Miller's (2013).mp4
Don't Breathe (2016).mkv
```

## Troubleshooting
If you encounter any issues while using IMDbMovieFileFixer, here are some common problems and solutions:

- **Python Version Error**: Ensure you have Python 3.6 or higher installed. You can check your Python version by running `python --version` in your terminal.
- **Missing Libraries**: If you get an ImportError, make sure all required libraries are installed by running `pip install requests beautifulsoup4`.
- **Folder Path Issues**: Verify that the folder path specified in the script exists and is correct. Ensure you have the necessary permissions to read and write in that directory.
- **File Not Found**: If the script logs "File not found," ensure the files are not being moved or deleted by another process while the script is running.
- **IMDb Search Issues**: If the script cannot find the official movie name on IMDb, check your internet connection and ensure IMDb is accessible. You might also want to verify the search URL and headers in the script.
- **Permission Denied**: If you encounter a "Permission Denied" error, ensure you have the necessary permissions to read, write, and rename files in the specified directory. You might need to run the script with elevated privileges (e.g., using `sudo` on Unix-based systems).
- **Rate Limiting**: If IMDb blocks your requests due to too many rapid requests, consider adding a longer delay between requests in the script. You can adjust the `time.sleep(1)` line to a higher value.
- **Incorrect Filename Format**: If the script does not recognize the format of your movie filenames, ensure they follow a consistent pattern that includes the movie name and year. You might need to adjust the regex pattern in the script to match your specific filename format.
- **Encoding Issues**: If you encounter encoding errors, ensure your script and files are using the same encoding (e.g., UTF-8). You can specify the encoding when opening files in Python by using `open(filename, 'r', encoding='utf-8')`.
- **Network Issues**: If the script fails to connect to IMDb, check your internet connection and ensure there are no network restrictions or firewalls blocking the requests.
- **Unexpected Errors**: For any other unexpected errors, check the log file for detailed error messages. You can also add more error handling in the script to catch and log specific exceptions.

## FAQ

### General Questions
**Q: What does the script do if it finds a duplicate filename?**  
A: The script appends an index to the new filename to ensure it is unique. For example, if "Movie (2023).mp4" already exists, the script will rename the duplicate to "Movie (2023) [1].mp4".

**Q: Can I use this script for TV shows or other types of media files?**  
A: The script is designed for movie files and may not work correctly with TV shows or other media types without modifications.

**Q: How can I contribute to this project?**  
A: Contributions are welcome! Please fork the repository, make your changes, and submit a pull request.

### Customization
**Q: Can I customize the grammar corrections?**  
A: Yes, you can customize the grammar corrections by modifying the `correct_grammar` function in the script. Add or remove patterns and replacements as needed.

**Q: How can I change the delay between IMDb requests?**  
A: You can change the delay by modifying the `time.sleep(1)` line in the script. Increase the value to add a longer delay between requests.

### Technical Issues
**Q: What happens if the IMDb search returns multiple results?**  
A: The script currently takes the first result from the IMDb search. If you need more precise matching, you might want to enhance the search logic to better filter results.

**Q: What should I do if the script stops working due to changes on the IMDb website?**  
A: If IMDb changes its website structure, the script might need updates to the HTML parsing logic. Check the `search_imdb` function and adjust the BeautifulSoup selectors accordingly.

**Q: How do I handle files with special characters in their names?**  
A: The script should handle most special characters, but if you encounter issues, you might need to add additional handling for specific characters in the renaming logic.

### Platform Compatibility
**Q: Can I run this script on Windows/Mac/Linux?**  
A: Yes, the script is platform-independent and should work on any operating system that supports Python. Just ensure you have the required libraries installed.

### Reverting Changes
**Q: Is there a way to preview changes before renaming files?**  
A: Currently, the script directly renames files. If you want to preview changes, you could modify the script to print the proposed new filenames instead of renaming them, and then manually review the output.

**Q: How can I revert the changes made by the script?**  
A: The script logs all changes in the output file. You can use this log to manually revert any changes if needed. Automating this process would require additional scripting.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request.

## License
This project is licensed under the GNU General Public License v3.0. See the LICENSE file for details.

## Acknowledgements
- BeautifulSoup
- Requests

## Contact
For support or any questions, please contact:
- **Michal Ferber**: support@michalferber.me
- **GitHub Issues**: GitHub Issues Page

## Related Resources
- IMDb
- Python Requests Library
- BeautifulSoup Documentation
