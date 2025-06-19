# LLM Web Summarizer - Basic OpenAI Connection Lab

## Overview

This Jupyter notebook is an educational lab from an LLM (Large Language Model) engineering course that teaches you how to build your first frontier LLM application. The project creates a **web browser summarizer** - give it any URL, and it will provide an intelligent summary using OpenAI's GPT models.

## What This Application Does

The notebook builds a complete web summarization tool that:

1. **Scrapes web content** from any given URL using BeautifulSoup
2. **Cleans and processes** the HTML content (removes scripts, styles, images)
3. **Sends the content to OpenAI's GPT-4o-mini** model for analysis
4. **Returns a markdown-formatted summary** of the website
5. **Handles both simple websites and news sites** with announcements

### Key Features
- Intelligent content extraction that ignores navigation elements
- Proper handling of system and user prompts for optimal LLM performance
- Markdown-formatted output for clean display
- Examples with real websites (CNN, Anthropic, Edward Donner's site)

## Prerequisites

### Technical Requirements
- **Python 3.7+** (recommended: Python 3.11+)
- **Jupyter Lab or Jupyter Notebook**
- **OpenAI API account** with valid API key
- **Internet connection** for web scraping and API calls

### Knowledge Requirements
- Basic Python programming knowledge
- Understanding of environment variables
- Familiarity with Jupyter notebooks (optional - guide included)

## Setup Instructions

### 1. Environment Setup

First, ensure you have Python and Jupyter installed. If you're new to this, the notebook references setup guides for [PC](../SETUP-PC.md) and [Mac](../SETUP-mac.md).

### 2. Install Required Dependencies

The notebook requires these Python packages:
```bash
pip install openai requests python-dotenv beautifulsoup4 ipython
```

### 3. OpenAI API Key Configuration

You **must** have an OpenAI API key to run this notebook:

1. **Get an API Key:**
   - Visit [OpenAI's API platform](https://platform.openai.com/api-keys)
   - Create an account if you don't have one
   - Generate a new API key (should start with `sk-proj-`)

2. **Create a .env File:**
   Create a file named `.env` in the same directory as this notebook:
   ```
   OPENAI_API_KEY=sk-proj-your-actual-api-key-here
   ```

3. **Important Security Notes:**
   - Never commit your .env file to version control
   - Keep your API key private
   - Monitor your API usage to control costs

### 4. Cost Considerations

- The notebook uses `gpt-4o-mini`, which is OpenAI's most cost-effective model
- Typical costs should be minimal (few cents per summary)
- You can monitor usage in your OpenAI dashboard
- For a free alternative, see the Ollama option mentioned in the notebook

## How to Run the Notebook

### 1. Launch Jupyter Lab
```bash
jupyter lab
```

### 2. Open the Notebook
Navigate to and open `Basic-Connect-OpenAI.ipynb`

### 3. Execute Cells in Order
- **Read the educational content** in markdown cells
- **Execute each code cell** by clicking it and pressing `Shift + Enter`
- **Follow along** with the examples provided

### 4. Key Execution Steps

1. **Import Libraries** (Cell 1)
2. **Load Environment Variables** (Cell 2) - Verify your API key is detected
3. **Test OpenAI Connection** (Cell 3) - Should return a simple greeting
4. **Create Website Class** (Cell 7) - For web scraping functionality
5. **Test Web Scraping** (Cell 10) - Try scraping a simple website
6. **Build Summarization Functions** (Cells 11-20) - Core functionality
7. **Test with Real Websites** (Cells 21-25) - See the magic happen!

## Detailed Code Walkthrough

### Core Components

1. **Website Class**
   ```python
   class Website:
       def __init__(self, url):
           # Scrapes website content
           # Extracts title and clean text
           # Removes scripts, styles, images
   ```

2. **Prompt Engineering**
   ```python
   system_prompt = "You are an assistant that analyzes websites..."
   user_prompt_for(website)  # Creates detailed user prompts
   ```

3. **OpenAI Integration**
   ```python
   def summarize(url):
       website = Website(url)
       response = openai.chat.completions.create(
           model="gpt-4o-mini",
           messages=messages_for(website)
       )
   ```

### Message Structure

The notebook teaches the standard OpenAI message format:
```python
[
    {"role": "system", "content": "system instructions"},
    {"role": "user", "content": "user query with website content"}
]
```

## Example Usage

After setup, you can summarize any website:

```python
# Basic usage
summary = summarize("https://example.com")
print(summary)

# Pretty display in Jupyter
display_summary("https://cnn.com")
```

## Limitations and Considerations

### Technical Limitations
- **JavaScript-heavy sites**: Won't work with React apps or heavily JS-rendered content
- **Protected sites**: CloudFront and similar protections may block access
- **Rate limiting**: Respect website rate limits and OpenAI API limits

### Suggested Improvements
- The notebook mentions Selenium implementation for JS sites (see community-contributions folder)
- Error handling for failed requests
- Caching to avoid re-scraping the same content

## Troubleshooting

### Common Issues

1. **API Key Problems**
   ```
   "No API key was found"
   ```
   - Check your .env file exists and has correct format
   - Ensure API key starts with `sk-proj-`
   - Remove any extra spaces around the key

2. **Import Errors**
   ```
   "ModuleNotFoundError"
   ```
   - Install missing packages: `pip install [package-name]`
   - Ensure you're in the correct Python environment

3. **Website Access Issues**
   ```
   "403 Forbidden" or "Connection timeout"
   ```
   - Some sites block automated access
   - Try different websites
   - Check your internet connection

4. **Kernel Issues**
   - Restart kernel: Kernel menu → Restart Kernel and Clear Outputs
   - Start fresh from the top of the notebook

## Business Applications

### Use Cases Demonstrated
- **Web content summarization** - News aggregation, research
- **Content analysis** - Competitive intelligence, market research
- **Information extraction** - Due diligence, fact-checking

### Potential Extensions
- **Email summarization** - Generate subject lines from email content
- **Document processing** - Summarize PDFs, reports, articles
- **Social media monitoring** - Track and summarize mentions
- **Research automation** - Gather and synthesize information from multiple sources

## Educational Value

This notebook teaches:
- **API integration** with frontier LLMs
- **Prompt engineering** best practices
- **Web scraping** fundamentals
- **Error handling** and troubleshooting
- **Business application** thinking

## Next Steps

After completing this lab:
1. **Experiment** with different websites and prompts
2. **Modify the system prompt** to change output style/language
3. **Try the suggested exercise** (email subject line generation)
4. **Explore advanced features** like different models or streaming
5. **Consider contributing** improvements to the community folder

## Support and Community

- **Course instructor**: Available at ed@edwarddonner.com
- **LinkedIn**: https://www.linkedin.com/in/eddonner/
- **Troubleshooting**: See the troubleshooting.ipynb notebook
- **Community contributions**: Submit pull requests for improvements

## Files Structure

```
project-root/
├── Basic-Connect-OpenAI.ipynb    # Main notebook
├── .env                          # Your API keys (create this)
├── troubleshooting.ipynb         # Troubleshooting guide
├── community-contributions/      # Student improvements
└── guides/                       # Additional learning resources
```

This lab represents your first step into frontier LLM engineering - by the end of the full course, you'll be building autonomous agentic AI solutions with multiple collaborating agents!