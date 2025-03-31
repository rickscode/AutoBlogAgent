# AutoBlogAgent

## Overview
The AutoBlogAgent is an automated blogging application designed to simplify the process of creating, managing, and publishing blog posts for the Asia Tech Academy. The application integrates with WordPress, Cloudflare AI, and SERP APIs to generate high-quality blog content, images, and meta descriptions, enhancing SEO and audience engagement.

---

## Features
- **Automated Blog Post Generation**: Uses LLM (e.g., Groq API) to create engaging blog posts based on the latest information gathered from the web.
- **Dynamic Title and Content Creation**: Generates titles and content tailored to specific queries and SEO requirements.
- **Image Generation**: Creates AI-generated images based on blog topics using Cloudflare AI.
- **WordPress Integration**: Automatically uploads blog posts and featured images to WordPress.
- **SEO-Ready Posts**: Ensures posts include titles, featured images, and categories for optimal SEO performance.
- **Manual Meta Description Update**: Meta descriptions are provided but require manual addition in WordPress due to API limitations.

---

## Prerequisites

### System Requirements
- Python 3.8+
- A WordPress site with REST API enabled

### API Keys & Access
- **WordPress**: Basic Authentication credentials
- **Cloudflare AI**: API token
- **SERP API**: API key
- **Groq API**: API key (for LLM integration)

### Install Dependencies
Create a virtual environment and install the required dependencies:

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## Environment Variables

Set up the `.env` file in the project root with the following variables:

```env
WP_APP_KEY=<WordPress Basic Auth Key>
WP_BASE_URL=<Your WordPress Base URL>
CLOUDFLARE_API_TOKEN=<Cloudflare API Token>
SERP_API_KEY=<SERP API Key>
GROQ_API_KEY=<Groq API Key>
```

---

## How to Run

### 1. Start the Application
Activate your virtual environment and run the script:

```bash
python blog_poster.py
```

### 2. Workflow
The application follows these steps:
1. **Search for Latest Information**: Uses SERP API to gather relevant data.
2. **Generate Content**: Uses LLM to create a title and blog content.
3. **Generate Images**: Creates AI-generated images for the blog post.
4. **Upload to WordPress**: Publishes the post with the featured image.
5. **Manual Meta Description**: Provides a meta description for manual addition in WordPress.

---

## Limitations
- **Meta Description Automation**: Due to Yoast SEO API limitations, meta descriptions must be added manually in WordPress.
- **Yoast SEO Integration**: Requires a custom PHP filter to fully utilize `_yoast_wpseo_metadesc`.

---

## File Structure
```plaintext
ATAAutoBlogger/
├── blog_poster.py       # Main application script
├── requirements.txt     # Python dependencies
├── .env                 # Environment variables (not included in repo)
├── README.md            # Documentation
└── utils/               # Utility functions and modules
```

---

## Future Enhancements
- Enable full automation of Yoast SEO meta descriptions via direct database updates or alternative plugins.
- Add support for scheduled posts using cron jobs.
- Implement robust error handling and logging.
- Expand AI capabilities for multi-language support.

---

## Troubleshooting

### Common Issues

1. **Image Upload Errors**:
   - Ensure the Cloudflare API token is valid.
   - Check WordPress media upload permissions.

2. **Meta Description Missing**:
   - Confirm the manual process for adding meta descriptions in WordPress.
   - Verify the custom PHP filter is correctly implemented.

3. **Authentication Errors**:
   - Double-check the `WP_APP_KEY` in the `.env` file.
   - Ensure WordPress REST API is enabled.

---

