# 🍌 Enhanced N8N Workflows - Complete Usage Guide

This guide provides comprehensive instructions for using the enhanced N8N workflows with proper GUIDs, improved structure, and optimized performance.

## 📋 Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Workflow Files](#workflow-files)
- [Installation & Setup](#installation--setup)
- [Individual Workflow Guides](#individual-workflow-guides)
- [Troubleshooting](#troubleshooting)
- [Customization](#customization)
- [Best Practices](#best-practices)

## 🎯 Overview

These enhanced workflows provide improved N8N automation capabilities with:
- ✅ Proper GUID management for all nodes and workflows
- ✅ Enhanced error handling and timeout configurations
- ✅ Optimized data processing and workflow structure
- ✅ Better naming conventions and documentation
- ✅ Comprehensive settings and metadata

## 🔧 Prerequisites

Before using these workflows, ensure you have:

1. **N8N Instance**: Running N8N (self-hosted or cloud)
2. **OpenRouter API Key**: For Gemini AI integration
3. **RunwayML API Key**: For image-to-video conversion (optional)
4. **Webhook Access**: For chat trigger functionality

## 📁 Workflow Files

| Workflow | File | Complexity | Nodes | Description |
|----------|------|------------|-------|-------------|
| **Image to Video** | `Banana_Image_to_Video_Enhanced.json` | Advanced | 6 | Generate images with Gemini and convert to videos |
| **Basic N8N** | `Banana_Basic_N8N_Enhanced.json` | Basic | 4 | Simple image generation workflow |
| **Google Banana** | `Google_Banana_N8N_Enhanced.json` | Basic | 4 | Enhanced Google Gemini integration |

## 🚀 Installation & Setup

### Step 1: Import Workflows

1. **Open your N8N instance**
2. **Navigate to Workflows**
3. **Click "Import from File"**
4. **Select the desired JSON file**
5. **Review and confirm import**

### Step 2: Configure Credentials

#### OpenRouter API Setup
```json
{
  "id": "your_openrouter_credential_id",
  "name": "OpenRouter API",
  "type": "openRouterApi",
  "data": {
    "apiKey": "your_api_key_here"
  }
}
```

#### RunwayML API Setup (for Image to Video workflow)
```json
{
  "id": "your_runwayml_credential_id",
  "name": "RunwayML API",
  "type": "genericCredentialType",
  "data": {
    "httpHeaderAuth": {
      "name": "Authorization",
      "value": "Bearer your_api_key_here"
    }
  }
}
```

### Step 3: Update Webhook IDs

Each workflow uses a unique webhook ID. Update these in your environment:

```json
"webhookId": "your_webhook_id_here"
```

## 📖 Individual Workflow Guides

### 🎬 Image to Video Workflow

**File**: `Banana_Image_to_Video_Enhanced.json`

**Purpose**: Generate images using Gemini AI and convert them to videos using RunwayML

**Workflow Flow**:
1. **Chat Trigger** → Receives user input
2. **Gemini AI** → Generates image based on prompt
3. **Data Processing** → Extracts and formats image data
4. **File Conversion** → Converts base64 to binary
5. **RunwayML API** → Converts image to video
6. **Response Formatting** → Returns video URL and status

**Configuration**:
- **Model**: `google/gemini-2.5-flash-image-preview:free`
- **Max Tokens**: 1000
- **Temperature**: 0.7
- **Timeout**: 30s (Gemini), 120s (RunwayML)

**Usage**:
1. Send a text prompt via chat
2. Wait for image generation
3. Image automatically converts to video
4. Receive video URL and status

### 🖼️ Basic N8N Workflow

**File**: `Banana_Basic_N8N_Enhanced.json`

**Purpose**: Simple image generation using Gemini AI

**Workflow Flow**:
1. **Chat Trigger** → Receives user input
2. **Gemini AI** → Generates image based on prompt
3. **Data Processing** → Extracts and formats image data
4. **File Conversion** → Converts to binary format

**Configuration**:
- **Model**: `google/gemini-2.5-flash-image-preview:free`
- **Max Tokens**: 1000
- **Temperature**: 0.7
- **Timeout**: 30s

**Usage**:
1. Send a text prompt via chat
2. Wait for image generation
3. Receive generated image in binary format

### 🌟 Google Banana Workflow

**File**: `Google_Banana_N8N_Enhanced.json`

**Purpose**: Enhanced Google Gemini integration with optimized processing

**Workflow Flow**:
1. **Chat Trigger** → Receives user input
2. **Gemini AI** → Generates image based on prompt
3. **Data Processing** → Extracts and formats image data
4. **File Conversion** → Converts to binary format

**Configuration**:
- **Model**: `google/gemini-2.5-flash-image-preview:free`
- **Max Tokens**: 1000
- **Temperature**: 0.7
- **Timeout**: 30s

**Usage**:
1. Send a text prompt via chat
2. Wait for image generation
3. Receive generated image in binary format

## 🔍 Troubleshooting

### Common Issues

#### 1. Credential Errors
**Problem**: "Invalid credentials" error
**Solution**: 
- Verify API keys are correct
- Check credential type matches workflow
- Ensure credentials are properly saved

#### 2. Webhook Issues
**Problem**: Chat trigger not working
**Solution**:
- Verify webhook ID is correct
- Check webhook is active
- Test webhook endpoint manually

#### 3. Timeout Errors
**Problem**: API calls timing out
**Solution**:
- Increase timeout values in workflow
- Check network connectivity
- Verify API service status

#### 4. Data Processing Errors
**Problem**: Field extraction failures
**Solution**:
- Verify API response structure
- Check field mapping in Set nodes
- Test with sample data

### Debug Steps

1. **Enable Debug Mode** in workflow settings
2. **Check Execution Logs** for detailed error information
3. **Test Individual Nodes** to isolate issues
4. **Verify Data Flow** between nodes
5. **Check API Documentation** for endpoint changes

## 🎨 Customization

### Modifying Workflow Parameters

#### Change AI Model
```json
"model": "google/gemini-2.5-flash-image-preview:free"
```
Replace with other available models:
- `google/gemini-2.0-flash-exp:free`
- `google/gemini-2.0-flash:free`
- `google/gemini-1.5-flash:free`

#### Adjust Generation Parameters
```json
"max_tokens": 1000,
"temperature": 0.7
```
- **Max Tokens**: Higher values for longer responses
- **Temperature**: Lower for focused, higher for creative

#### Modify Timeouts
```json
"timeout": 30000
```
Adjust based on your needs and API response times.

### Adding New Nodes

1. **Insert Node** at desired position
2. **Update Connections** in workflow
3. **Generate New GUID** for the node
4. **Test Data Flow** to ensure compatibility

## 📚 Best Practices

### 1. **GUID Management**
- Always generate unique GUIDs for new nodes
- Use consistent GUID format
- Avoid reusing GUIDs across workflows

### 2. **Error Handling**
- Set appropriate timeout values
- Implement error workflows where needed
- Add validation nodes for critical data

### 3. **Performance Optimization**
- Use appropriate node types for data processing
- Minimize unnecessary data transformations
- Implement proper data filtering

### 4. **Security**
- Store API keys securely
- Use environment variables for sensitive data
- Regularly rotate API credentials

### 5. **Monitoring**
- Enable execution progress tracking
- Monitor workflow performance
- Set up alerts for failures

## 🔄 Workflow Updates

### Version Control
- Keep backup copies of working workflows
- Document changes and improvements
- Test updates in development environment

### Migration Steps
1. **Export current workflow**
2. **Import enhanced version**
3. **Update credentials and webhooks**
4. **Test functionality**
5. **Deploy to production**

## 📞 Support

### Getting Help
1. **Check N8N Documentation**: [docs.n8n.io](https://docs.n8n.io)
2. **Community Forum**: [community.n8n.io](https://community.n8n.io)
3. **GitHub Issues**: Report bugs and request features

### Contributing
- Share workflow improvements
- Report issues with detailed information
- Contribute to workflow templates

## 📄 License

These enhanced workflows are provided as-is for educational and development purposes. Please ensure compliance with:
- N8N terms of service
- API provider terms
- Local data protection regulations

---

**Last Updated**: January 30, 2025  
**Version**: 2.0.0  
**Author**: Enhanced N8N Workflows

---

*Happy automating! 🚀*
