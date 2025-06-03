# Cursor Rules & Tools

A comprehensive toolkit for AI-powered development, image processing, web scraping, and automation. This project provides utility tools that integrate with various AI services and APIs.

## 🚀 Quick Setup

### 1. Install Dependencies
```bash
npm install
```

### 2. Configure Environment Variables
Copy the example environment file and add your API keys:
```bash
cp .env.example .env.local
```

Edit `.env.local` with your API keys:
```bash
# Required for Gemini AI tools
GOOGLE_AI_STUDIO_KEY=your_google_ai_studio_key_here

# Required for OpenAI image generation
OPENAI_API_KEY=your_openai_api_key_here

# Required for video generation and AI background removal
REPLICATE_API_TOKEN=your_replicate_api_token_here
```

### 3. API Key Setup Instructions

#### Google AI Studio Key (Gemini)
1. Visit [Google AI Studio](https://ai.google.dev/)
2. Create a new project or select existing
3. Generate an API key
4. Add to `.env.local` as `GOOGLE_AI_STUDIO_KEY`

#### OpenAI API Key
1. Visit [OpenAI Platform](https://platform.openai.com/)
2. Navigate to API Keys section
3. Create a new API key
4. Add to `.env.local` as `OPENAI_API_KEY`

#### Replicate API Token
1. Visit [Replicate](https://replicate.com/)
2. Sign up/login and go to Account settings
3. Generate an API token
4. Add to `.env.local` as `REPLICATE_API_TOKEN`

## 🛠️ Available Tools

### Image Generation & Processing

#### Gemini Image Generation
Generate images using Google's Imagen 3.0 or Gemini 2.0:
```bash
npm run gemini-image -- generate -p "A futuristic workspace" -m imagen-3.0 --folder public/images
```

#### OpenAI Image Generation  
Generate images using GPT-image-1 or DALL-E 3:
```bash
npm run openai-image -- generate -p "A robot assistant" --folder public/images
```

#### Image Optimization
Resize, convert formats, and remove backgrounds:
```bash
npm run optimize-image -- -i input.png -o output.webp --resize 512x512 --format webp --quality 90
```

#### Advanced Background Removal
Remove backgrounds using edge detection:
```bash
npm run remove-background-advanced -- --input image.png --output result.png --tolerance 40
```

### AI & Text Processing

#### Gemini API
Chat with Gemini, analyze documents, and get grounded search results:
```bash
# Basic chat
npm run gemini -- --prompt "Explain quantum computing"

# Grounded search with real-time data
npm run gemini -- --prompt "Latest AI developments 2025" --ground --show-search-data

# Structured JSON output
npm run gemini -- --prompt "List programming languages" --json custom --schema '{"type":"array","items":{"type":"object","properties":{"language":{"type":"string"},"description":{"type":"string"}},"required":["language","description"]}}'

# Document analysis
npm run gemini -- --prompt "Summarize this document" --file document.pdf

# Image analysis
npm run gemini -- --prompt "Describe this image" --image photo.jpg
```

### Web & File Tools

#### HTML to Markdown
Scrape websites and convert to Markdown:
```bash
npm run html-to-md -- --url https://example.com --output content.md --selector main
```

#### File Downloader
Download files with progress tracking:
```bash
npm run download-file -- --url https://example.com/file.jpg --folder downloads --filename myfile.jpg
```

#### Video Generation
Generate videos using various AI models:
```bash
npm run generate-video -- --prompt "A rotating cube" --model minimax --duration 3 --output cube.mp4
```

### Development Tools

#### GitHub CLI Integration
Manage repositories, PRs, and issues:
```bash
npm run github -- pr-create --title "New feature" --body "Description"
npm run github -- issue-list --state open
npm run github -- repo view
```

## 📁 Project Structure

```
cursor-rules-tools/
├── .cursorrules          # Cursor AI rules and tool definitions
├── .env.example          # Environment variables template
├── package.json          # Dependencies and scripts
├── tools/                # Utility scripts
│   ├── gemini.ts         # Gemini API integration
│   ├── gemini-image-tool.js # Image generation with Gemini
│   ├── openai-image-tool.js # OpenAI image generation
│   ├── image-optimizer.ts   # Image processing with Sharp
│   ├── html-to-md.ts        # Web scraping to Markdown
│   ├── download-file.ts     # File download utility
│   └── generate-video.ts    # AI video generation
├── public/
│   ├── images/           # Generated/processed images
│   └── videos/           # Generated videos
└── README.md            # This file
```

## 🔧 Development

### Running Tools Directly
You can run tools directly with tsx:
```bash
npx tsx tools/gemini.ts --prompt "Hello world"
npx tsx tools/image-optimizer.ts -i input.png -o output.webp
```

### Adding New Tools
1. Create your tool in the `tools/` directory
2. Add npm script to `package.json`
3. Update `.cursorrules` command_line_tools section
4. Test and document in this README

## 📚 Documentation

For detailed information about rules and tool configurations, see:
- `@.cursorrules` - Cursor AI rules and tool definitions
- `@package.json` - Available scripts and dependencies
- `@tools/` - Individual tool scripts and their usage

## 🎯 Use Cases

- **Content Creation**: Generate images, videos, and convert web content to Markdown
- **Development Workflow**: Integrate AI assistance into your development process
- **Image Processing**: Optimize, resize, and enhance images for web/mobile
- **Research**: Use grounded search to get up-to-date information
- **Automation**: Automate repetitive tasks with AI-powered tools

## 🚨 Important Notes

- Tools are designed for development environment (`NODE_ENV=development`)
- API usage may incur costs depending on your usage and provider plans
- Keep your API keys secure and never commit them to version control
- Some tools require internet connectivity for AI service access

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add or improve tools
4. Update documentation
5. Submit a pull request

## 📄 License

See LICENSE file for details.
