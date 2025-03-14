# Video Pipeline with Kafka, S3, and FFmpeg

This project builds a video pipeline that leverages Kafka for stream processing, S3 for storage, and `ffmpeg` for video file conversion. Developed using TypeScript and Node.js, the pipeline facilitates downloading, processing, and storing video files in various formats.

## Project Overview

The aim of this lab is to create a pipeline that:
1. **Downloads video files** using tools such as `yt-dlp`.
2. **Uploads the video files** to an S3 storage service.
3. **Processes the video files** using `ffmpeg` to convert them into various formats.
4. **Utilizes Kafka** for messaging between different components of the pipeline.

## Technologies Used

- **TypeScript**: The main programming language for this project.
- **Node.js**: The runtime environment for executing the code.
- **Kafka**: A messaging system for handling parallel file processing.
- **S3**: A storage solution for saving video files.
- **ffmpeg**: A tool for video processing and file conversion.
- **yt-dlp**: A tool for downloading videos from platforms like YouTube.

## Getting Started

Follow the steps below to set up and run the project on your local machine:

### 1. Clone the Repository

First, clone the repository to your desired directory:

```bash
git clone <https://github.com/cernatina/VideoPipeline.git>
cd <video-pipeline-lab>
```
2. Install Dependencies
Install the required dependencies using npm or yarn:

```bash
npm install
```

3. Configure Kafka and S3
Make sure Kafka and S3 are correctly configured. Modify the configuration file to include the necessary authentication details for Kafka and S3.

4. Install yt-dlp and ffmpeg
You will need the following tools to download and process video files:

yt-dlp: Installation instructions for yt-dlp.
ffmpeg: Installation instructions for ffmpeg.
Once installed, verify that both tools are accessible via your system's PATH.

5. Run the Application
Once all dependencies and configurations are in place, you can start the application:

Start the Producer to Download Videos
```bash
ts-node videoPipeline.ts producer
```
Start the Consumer to Process Videos
```bash
ts-node videoPipeline.ts consumer
```
# Workflow
## Producer:

Downloads videos from platforms like YouTube using yt-dlp.

Uploads the downloaded files to S3.

Sends a Kafka message indicating that a video is ready for processing.

## Consumer:

Listens for Kafka messages with information about the uploaded videos.

Downloads the video files from S3.

Uses ffmpeg to convert the videos into different formats (e.g., mp4, avi, webm, mkv).

Uploads the processed files back to S3.

Removes temporary files after processing.
