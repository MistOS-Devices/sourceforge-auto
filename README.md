# Using the Gofile to SourceForge Workflow

This workflow downloads a main file from Gofile and uploads it to SourceForge. You can also upload multiple optional files in the same run.

## Run the pipeline

1. Open your GitHub repository and go to **Actions**.
2. Select **Gofile to SourceForge**.
3. Click **Run workflow**.
4. Fill in the inputs below.
5. Click **Run workflow** to start the upload.
6. Open the workflow run to watch the progress and check the final result.

## Fill in the inputs

- **Gofile URL (`gofile_url`) — required:** Paste the Gofile link for the main ROM or file.
- **Device (`device`) — required:** Enter the target device folder, for example `raven`.
- **Optional Gofile URLs (`extra_gofile_urls`) — optional:** Paste links for additional files, such as `boot.img`, `vendor_boot.img`, or recovery images. This is a single-line field, so separate multiple URLs with commas.
- **Optional folder (`extra_folder`) — optional:** Enter a subfolder for the optional files, for example `5.1-IMG`. Leave it empty to put optional files directly in the device folder.

### Example inputs

| Input | Example |
|---|---|
| Gofile URL | `https://gofile.io/d/PRIMARYID` |
| Device | `raven` |
| Optional Gofile URLs | `https://gofile.io/d/R5Ouyjuy, https://gofile.io/d/BlRG1H1A, https://gofile.io/d/sbcxWQ4o` |
| Optional folder | `5.1-IMG` |

**Important:** Use plain Gofile URLs separated by commas in the optional URL field. Do not press Enter between links because GitHub starts the workflow when Enter is pressed.

## Where files are uploaded

The main file is uploaded to:

```text
Android17/<device>/
```

Optional files are uploaded to:

```text
Android17/<device>/<extra_folder>/
```

If the optional folder is left empty, optional files go directly into `Android17/<device>/`.

For example, with device `raven` and folder `5.1-IMG`, optional files go into:

```text
Android17/raven/5.1-IMG/
```

## Check the result

After starting the workflow:

1. Open the running job in **Actions**.
2. Review the logs for the Gofile download and SourceForge upload steps.
3. Confirm that upload verification succeeds and review the final result for the destination path and file details.

If the run fails, open the failed step and read its error message. Make sure the links are correct and the device/folder names are spelled as intended.
