# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Common Commands

### Development
- **Run a tool directly**: `npx tsx tools/<tool-name>.ts`
- **Run tool via npm script**: `npm run <script-name>`

### Available NPM Scripts for Tools

#### AI & Text Processing
- `npm run gemini` - Chat with Gemini, analyze documents, grounded search
- `npm run openai-image` - Generate images using OpenAI (DALL-E 3)
- `npm run gemini-image` - Generate images using Gemini (Imagen 3.0)

#### Image Processing
- `npm run optimize-image` - Resize, convert formats, optimize images with Sharp
- `npm run remove-background-advanced` - Remove backgrounds using edge detection
- `npm run invert-colors` - Invert image colors
- `npm run recraft` - Recraft image generation
- `npm run flux` - Flux image generation
- `npm run imagen` - Google Imagen generation
- `npm run minimax-image` - Minimax image generation

#### Web & File Tools
- `npm run html-to-md` - Scrape websites and convert to Markdown
- `npm run download-file` - Download files with progress tracking
- `npm run generate-video` - Generate videos using AI models

#### GitHub Integration
- `npm run github` - GitHub CLI integration for repos, PRs, issues
- `npm run github:pr-create` - Create a pull request
- `npm run github:issue-list` - List GitHub issues

## Architecture

### Tool Structure
All tools are TypeScript modules in the `tools/` directory. Each tool:
- Is a standalone TypeScript file that can be executed with tsx
- Uses commander or yargs for CLI argument parsing
- Requires environment variables for API keys (stored in `.env.local`)
- Outputs results to console or specified directories

### Key Dependencies
- **@google/generative-ai**: Google Gemini API integration
- **openai**: OpenAI API for image generation
- **sharp**: Image processing and optimization
- **replicate**: AI model hosting for video generation
- **turndown**: HTML to Markdown conversion
- **commander/yargs**: CLI argument parsing

### Environment Configuration
Tools run with `NODE_ENV=development` and require API keys in `.env.local`:
- `GOOGLE_AI_STUDIO_KEY`: For Gemini tools
- `OPENAI_API_KEY`: For OpenAI image generation
- `REPLICATE_API_TOKEN`: For video generation and advanced background removal

### Output Directories
- `public/images/`: Generated/processed images
- `public/videos/`: Generated videos
- Downloaded files go to specified folders via `--folder` parameter

## Cursor Rules Integration

The `.cursorrules` file defines workflows and behavioral patterns for AI assistants:
- Uses a structured workflow system (`<research>`, `<develop>`, `<validate>`, etc.)
- Tools are invoked via npm scripts defined in package.json
- Emphasizes context-rich prompts when using tools like `edit_file` and `run_terminal_cmd`

## Testing & Validation

Currently no automated tests are configured. Tools are tested manually via CLI execution.