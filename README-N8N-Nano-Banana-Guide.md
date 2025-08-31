# 🍌 N8N + Google Nano Banana: Complete AI Image & Video Generation Guide

> **Transform N8N into a powerful AI image and video generation tool using Google's latest Nano Banana technology**

## 🚀 Quick Start

This guide shows you how to:
- Generate high-quality images using Google Nano Banana (free via OpenRouter)
- Convert images to videos using Runway ML
- Create public chatbots for image generation
- Build automated workflows for content creation

## 📋 Prerequisites

- [N8N instance](https://n8n.io/) (self-hosted or cloud)
- [OpenRouter API key](https://openrouter.ai/) (free tier available)
- [Runway ML API key](https://dev.runway.ml/) (for video generation)
- Basic understanding of N8N workflows

## 🔑 API Setup

### 1. OpenRouter Setup (Free Image Generation)
1. Visit [openrouter.ai](https://openrouter.ai)
2. Go to **Keys** → **Create API Key**
3. Copy your API key
4. In N8N, create credential type: `OpenRouter`
5. Paste your API key

### 2. Runway ML Setup (Video Generation)
1. Visit [dev.runway.ml](https://dev.runway.ml)
2. Go to **API Keys** → **New API Key**
3. Copy your API key
4. In N8N, create credential type: `Generic Credential Type Header`
5. Set name: `Authorization`, value: `Bearer YOUR_API_KEY`

## 🎨 Basic Image Generation Workflow

### Workflow Structure
```
Chat Trigger → HTTP Request (OpenRouter) → Edit Fields → Convert to File
```

### Step-by-Step Setup

#### 1. Chat Trigger
- Add **Chat Trigger** node
- Configure for your N8N instance

#### 2. HTTP Request (OpenRouter)
- **Method**: POST
- **URL**: `https://openrouter.ai/api/v1/chat/completions`
- **Credential Type**: OpenRouter
- **Body** (JSON):
```json
{
  "model": "google/gemini-2.5-flash-image-preview-free",
  "messages": [
    {
      "role": "user",
      "content": "{{ $json.message }}"
    }
  ]
}
```

#### 3. Edit Fields
- Extract `data` string from OpenRouter response
- Map to clean output for image generation

#### 4. Convert to File
- **Operation**: Move Base64 String to File
- **Output**: Base64 image file
- **File Type**: Image

## 🎬 Image to Video Workflow

### Workflow Structure
```
Chat Trigger → HTTP Request (OpenRouter) → HTTP Request (Runway) → Get Video
```

### Additional Steps

#### 1. HTTP Request (Runway ML)
- **Method**: POST
- **URL**: `https://api.runwayml.com/v1/inference`
- **Headers**: 
  - `Authorization: Bearer YOUR_API_KEY`
  - `X-Runway-Version: 1.0`
- **Body** (JSON):
```json
{
  "model": "gen-3",
  "input": {
    "image": "{{ $json.image_url }}",
    "prompt": "Animate this image"
  }
}
```

#### 2. Get Video Result
- **Method**: GET
- **URL**: `https://api.runwayml.com/v1/inference/{{ $json.id }}`
- **Headers**: Same as above

## 🌟 Advanced Features

### 1. Public Chatbot
- Make workflow publicly available
- Share chatbot URL with others
- Generate images on demand

### 2. Custom Image Prompts
Use structured prompts for better results:
```json
{
  "subject": "Cat playing basketball",
  "composition": "Dynamic action shot",
  "style": "Photorealistic",
  "lighting": "Studio lighting",
  "mood": "Energetic and fun"
}
```

### 3. Style Presets
Apply consistent styling using JSON templates:
- **Game Style**: Cartoon/anime aesthetic
- **Photorealistic**: High-quality realistic images
- **Comic Book**: Graphic novel style
- **Artistic**: Creative/abstract interpretations

## 📊 Performance Comparison

| Feature | Google Nano Banana | ChatGPT DALL-E |
|---------|-------------------|----------------|
| **Speed** | ⚡ 10-50x faster | 🐌 Slow |
| **Quality** | 🎯 High quality | ✅ Good |
| **Editing** | ✏️ Real-time edits | ❌ Limited |
| **Cost** | 💰 Free via OpenRouter | 💸 Expensive |
| **Video Generation** | 🎬 Built-in support | ❌ Not available |

## 🔧 Troubleshooting

### Common Issues

#### 1. API Key Errors
- Verify credential type names match exactly
- Check API key format (Bearer + space + key)
- Ensure sufficient credits on Runway ML

#### 2. Image Generation Fails
- Use the free model: `google/gemini-2.5-flash-image-preview-free`
- Check prompt length and content
- Verify OpenRouter account status

#### 3. Video Generation Issues
- Ensure Runway ML account has credits
- Check image URL accessibility (must be public)
- Verify API endpoint and version headers

## 📁 Workflow Templates

### Available Templates
1. **Basic Image Generation** - Simple image creation
2. **Image to Video** - Convert images to animated videos
3. **Enhanced Prompts** - Better quality image generation
4. **Style Presets** - Consistent artistic styling

### Import Instructions
1. Download JSON template files
2. In N8N: **Import from File**
3. Upload JSON file
4. Configure API credentials
5. Test workflow

## 🚀 Pro Tips

### 1. Optimize Prompts
- Use descriptive, specific language
- Include style and composition details
- Reference the custom GPT prompt generator

### 2. Batch Processing
- Create multiple image variations
- Use different style presets
- Generate content series efficiently

### 3. Integration Ideas
- Connect to social media platforms
- Automate thumbnail generation
- Create marketing content workflows
- Build content creation pipelines

## 💡 Use Cases

### Content Creation
- **YouTube Thumbnails**: Generate eye-catching thumbnails
- **Social Media**: Create engaging visual content
- **Marketing**: Design promotional materials
- **Blog Posts**: Generate featured images

### Business Automation
- **E-commerce**: Product image variations
- **Real Estate**: Property visualization
- **Education**: Learning material creation
- **Healthcare**: Medical illustration

## 🔗 Resources

### Official Links
- [N8N Documentation](https://docs.n8n.io/)
- [OpenRouter API](https://openrouter.ai/docs)
- [Runway ML Developer Portal](https://dev.runway.ml/)
- [Google AI Studio](https://aistudio.google.com/)

### Community
- [N8N Community](https://community.n8n.io/)
- [AI Profit Boardroom](https://aiprofitboardroom.com/)
- [YouTube Channel](https://www.youtube.com/@JulianGoldieSEO)

## 📝 License

This guide is provided for educational purposes. Please respect API usage limits and terms of service for all third-party services.

## 🤝 Support

For workflow-specific help:
1. Check the troubleshooting section
2. Review API documentation
3. Join N8N community forums
4. Contact AI automation experts

---

**🎯 Ready to transform your N8N instance into an AI powerhouse? Start with the basic image generation workflow and build up to complex video generation pipelines!**

*Last updated: January 2025*
