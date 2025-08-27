# Reddit Newsletter Generator - N8N Workflow

This N8N workflow automatically generates daily newsletters from Reddit posts using AI, web scraping, and automated publishing. It's based on the live build demonstration from the N8N + Bright Data livestream.

## 🎯 What This Workflow Does

1. **RSS Feed Processing**: Reads the N8N subreddit RSS feed to get daily posts
2. **Web Scraping**: Uses Bright Data to scrape detailed content and comments from each Reddit post
3. **Data Processing**: Aggregates and formats the scraped data for AI processing
4. **AI Content Generation**: Uses OpenAI to create a professional newsletter in HTML format
5. **Multi-Platform Publishing**: Sends the newsletter via email and publishes to Dev.to

## 🚀 Features

- **Automated Reddit Monitoring**: Daily collection of posts from r/n8n
- **Intelligent Content Extraction**: Captures titles, descriptions, URLs, upvotes, and comments
- **AI-Powered Summarization**: Generates engaging newsletter content using GPT models
- **Professional Formatting**: Creates HTML newsletters with proper structure and styling
- **Multi-Channel Distribution**: Email delivery and Dev.to publishing
- **Error Handling**: Robust polling mechanism for Bright Data batch processing

## 📋 Prerequisites

### Required N8N Nodes
- **RSS Read Node**: Built into N8N
- **Bright Data Node**: Install from the N8N marketplace
- **OpenAI Node**: Install from the N8N marketplace
- **Gmail Node**: Built into N8N
- **Dev.to Node**: Install from the N8N marketplace

### Required Accounts & API Keys
- **Bright Data Account**: For web scraping capabilities
- **OpenAI API Key**: For AI content generation
- **Gmail Account**: For sending newsletters
- **Dev.to Account**: For publishing articles

## ⚙️ Setup Instructions

### 1. Install Required Nodes

In your N8N instance, go to **Settings > Community Nodes** and install:
- Bright Data
- OpenAI
- Dev.to

### 2. Configure Authentication

#### Bright Data
1. Create a Bright Data account at [brightdata.com](https://brightdata.com)
2. Get your API credentials
3. In N8N, go to **Credentials > Bright Data**
4. Add your username and password

#### OpenAI
1. Get an API key from [platform.openai.com](https://platform.openai.com)
2. In N8N, go to **Credentials > OpenAI API**
3. Add your API key

#### Gmail
1. In N8N, go to **Credentials > Gmail OAuth2**
2. Follow the OAuth2 setup process
3. Authorize your Gmail account

#### Dev.to
1. Get your API key from [dev.to/settings/account](https://dev.to/settings/account)
2. In N8N, go to **Credentials > Dev.to**
3. Add your API key

### 3. Import the Workflow

1. Download the `reddit-newsletter-workflow.json` file
2. In N8N, go to **Workflows > Import from File**
3. Select the downloaded JSON file
4. The workflow will be imported with all nodes and connections

### 4. Configure the Workflow

#### Update Email Recipient
1. Open the **Send Email** node
2. Change `your-email@example.com` to your actual email address

#### Customize Reddit Subreddit (Optional)
1. Open the **RSS Reader** node
2. Change the URL to any subreddit you want to monitor
3. Format: `https://www.reddit.com/r/SUBREDDIT_NAME/.rss`

#### Adjust AI Model (Optional)
1. Open the **AI Newsletter Generator** node
2. Change the model from `gpt-3.5-turbo` to your preferred model
3. Adjust the system prompt as needed

## 🔄 How It Works

### Workflow Flow
```
Manual Trigger → RSS Reader → Extract URLs → Aggregate URLs → Bright Data Scraper
                                                                    ↓
Publish to Dev.to ← Send Email ← AI Newsletter Generator ← Aggregate All Posts
```

### Detailed Process

1. **Trigger**: Manual execution (can be changed to scheduled)
2. **RSS Reading**: Fetches latest posts from Reddit RSS feed
3. **URL Extraction**: Extracts individual post URLs from RSS data
4. **URL Aggregation**: Combines all URLs into a single batch request
5. **Web Scraping**: Bright Data scrapes each Reddit post for detailed content
6. **Status Polling**: Continuously checks if scraping is complete
7. **Data Processing**: Extracts essential information and formats for AI
8. **AI Generation**: OpenAI creates a professional newsletter
9. **Distribution**: Sends email and publishes to Dev.to

### Key Features Explained

#### Bright Data Integration
- **Batch Processing**: Sends all URLs at once for efficient processing
- **Status Polling**: Automatically waits for scraping to complete
- **Error Handling**: Retries failed requests automatically
- **Anti-Bot Protection**: Bypasses common blocking mechanisms

#### AI Content Generation
- **Structured Prompts**: Ensures consistent newsletter format
- **Context Preservation**: Includes post details, comments, and engagement metrics
- **HTML Output**: Generates properly formatted newsletters
- **Professional Tone**: Creates engaging, readable content

#### Data Aggregation
- **Efficient Processing**: Reduces multiple items to single objects
- **Token Optimization**: Minimizes AI input costs
- **Clean Formatting**: Prepares data for optimal AI processing

## 🎨 Customization Options

### Newsletter Style
- Modify the AI system prompt in the **AI Newsletter Generator** node
- Adjust HTML formatting preferences
- Change section names (Top Stories, Community Buzz, Quick Hits)

### Content Sources
- Change the RSS feed URL to monitor different subreddits
- Add multiple RSS feeds for broader coverage
- Include other social media platforms

### Publishing Options
- Add more publishing destinations (Slack, Discord, etc.)
- Customize email templates
- Modify Dev.to article formatting

### Scheduling
- Change from manual trigger to scheduled execution
- Set up daily, weekly, or custom intervals
- Add time-based filtering

## 🚨 Troubleshooting

### Common Issues

#### Bright Data Timeout
- Increase wait time between status checks
- Check your Bright Data account limits
- Verify API credentials

#### OpenAI Rate Limits
- Switch to a different model
- Add retry logic
- Check API key validity

#### Gmail Authentication
- Re-authenticate OAuth2 credentials
- Check Gmail security settings
- Verify account permissions

#### RSS Feed Issues
- Verify subreddit exists and is public
- Check RSS feed accessibility
- Test feed URL in browser

### Debug Tips
- Use the **Execute Node** feature to test individual nodes
- Check execution logs for detailed error messages
- Verify data flow between nodes using the data viewer
- Test with smaller datasets first

## 📊 Performance Considerations

### Optimization Tips
- **Batch Size**: Keep Reddit post batches under 50 for optimal performance
- **AI Model**: Use faster models for real-time processing
- **Caching**: Pin successful executions to avoid re-scraping
- **Rate Limiting**: Respect API rate limits and add appropriate delays

### Resource Usage
- **Memory**: Large comment datasets may require more memory
- **API Costs**: Monitor OpenAI and Bright Data usage
- **Storage**: Consider archiving old newsletters
- **Network**: Ensure stable internet connection for web scraping

## 🔒 Security & Privacy

### Data Handling
- Only scrapes publicly available Reddit content
- No personal information is collected
- Respects Reddit's terms of service
- Uses official APIs where possible

### API Security
- Store API keys securely in N8N credentials
- Use environment variables for sensitive data
- Regularly rotate API keys
- Monitor API usage for anomalies

## 📈 Scaling & Production

### For Production Use
- Implement proper error handling and logging
- Add monitoring and alerting
- Use production-grade AI models
- Implement backup and recovery procedures

### For High-Volume Usage
- Consider using webhook callbacks instead of polling
- Implement queue-based processing
- Add load balancing for multiple instances
- Use dedicated infrastructure for web scraping

## 🤝 Contributing

This workflow is based on the N8N + Bright Data livestream demonstration. Feel free to:
- Improve error handling
- Add new publishing destinations
- Optimize performance
- Enhance AI prompts
- Add new data sources

## 📚 Additional Resources

- [N8N Documentation](https://docs.n8n.io/)
- [Bright Data Documentation](https://brightdata.com/docs)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [Dev.to API Documentation](https://developers.forem.com/api)

## 📄 License

This workflow is provided as-is for educational and development purposes. Please ensure compliance with all applicable terms of service and API usage policies.

---

**Built with ❤️ using N8N, Bright Data, and OpenAI**
