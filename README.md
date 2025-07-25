
# Automated Ad Performance Insights & Notifications

## Overview

A production-ready, enterprise-level automation system that automatically analyzes Google Ads performance data, provides AI-powered insights, and sends intelligent notifications based on performance trends. Built with comprehensive error handling and real-world scenario management.

![image](https://github.com/user-attachments/assets/709935d9-98c3-4127-965c-07b23986ce03)

## Key Features

### **Core Functionality**
- **Automatic Triggering**: Responds to new data in Google Sheets
- **AI-Powered Analysis**: Uses Google Gemini AI for intelligent performance insights
- **Smart Notifications**: Conditional Slack alerts based on performance status
- **Data Validation**: Comprehensive input validation with error handling
- **Historical Context**: Week-over-week comparison or industry benchmarks

###  **Robustness & Reliability**
- **What-If Logic**: Handles all edge cases gracefully
- **Retry Mechanisms**: Automatic retry on AI failures
- **Fallback Systems**: Manual review channels for unexpected scenarios
- **Error Monitoring**: Comprehensive error tracking and alerting
- **Data Quality Checks**: Validates input data before processing

### **Performance Analysis**
- **Week-over-Week Comparison**: When previous week data is available
- **Industry Benchmarks**: When historical data is missing
- **Structured Insights**: Consistent JSON output format
- **Actionable Recommendations**: Specific optimization suggestions

## 🏗️ Architecture

### **Phase 1: Data Validation & Quality Check**
- Validates incoming Google Sheets data
- Checks for missing fields, invalid types, and #REF! errors
- Routes invalid data to error notification channel

### **Phase 2: Context Preparation & AI Analysis**
- Fetches historical data for context
- Prepares data for AI analysis
- Handles missing previous week data gracefully

### **Phase 3: AI Performance Analysis**
- Leverages Google Gemini AI for intelligent analysis
- Provides structured insights and recommendations
- Supports both comparison and benchmark analysis

### **Phase 4: AI Output Validation & What-If Logic**
- Validates AI output structure and content
- Implements retry logic for failed AI responses
- Routes invalid outputs to manual review

### **Phase 5: Sheet Writeback & Conditional Notifications**
- Updates Google Sheets with AI insights
- Sends appropriate Slack notifications based on performance
- Handles all notification scenarios

## 🔧 Technical Specifications

### **Platform**
- **Built on**: n8n (Node.js-based workflow automation)
- **AI Model**: Google Gemini 2.0 Flash
- **Integrations**: Google Sheets, Slack, Google Gemini API

### **Data Requirements**
**Required Google Sheets Columns:**
- Week (numeric)
- Campaign Name (text)
- Status (text)
- Budget (€) (numeric)
- CTR (%) (numeric)
- Clicks (numeric)
- CPC (€) (numeric)
- Cost (€) (numeric)
- Conversions (numeric)
- Impression Share (%) (numeric)

### **Output Format**
**AI Analysis Output:**
```json
{
  "interpretation": "Performance analysis summary (max 200 words)",
  "recommendations": ["Actionable recommendation 1", "Actionable recommendation 2"]
}
```

## 📱 Notification System

### **Slack Channels**
1. **Stable Performance** (`#for-stable-good-updates`)
   - Triggered when performance is stable/improved
   - Green circle emoji, positive messaging

2. **Action Required** (`#marketing-action-items`)
   - Triggered when optimization is needed
   - Red circle emoji, actionable recommendations

3. **Error Handling** (`#workflow-errors`)
   - Data validation failures
   - AI analysis failures
   - System-level errors

### **Message Examples**

**Stable Performance:**
```
🟢 Weekly Ad Performance Update - Stable Performance

Campaign: Campaign 1
Week: 1
Analysis Context: week-over-week

AI Summary: Week 27 shows stable performance with CTR at 2.5%...

✅ All systems go! Performance is stable this week.
```

**Action Required:**
```
🔴 Action Required: Weekly Ad Performance Alert!

Campaign: Campaign 1
Week: 1
Analysis Context: industry-benchmarks

AI Summary: CTR at 1.2% is below industry average...

Recommendations:
• 1. Optimize ad copy to improve click-through rates
• 2. Review keyword targeting for better relevance

🚨 Let's review this ASAP and take action.
```

## 🚀 What-If Scenarios Handled

### **Data Quality Issues**
- ✅ Missing required fields → Error notification
- ✅ Invalid data types → Error notification
- ✅ #REF! errors → Error notification
- ✅ Empty values → Error notification

### **AI Analysis Issues**
- ✅ Invalid JSON output → Retry logic (2 attempts)
- ✅ Missing required fields → Fallback to manual review
- ✅ Malformed structure → Fallback to manual review
- ✅ API failures → Fallback to manual review
- ✅ Ambiguous output → Manual review channel

### **Context Issues**
- ✅ Missing previous week data → Industry benchmarks
- ✅ Multiple campaigns → Campaign-specific matching
- ✅ Data gaps → Graceful degradation

### **System Issues**
- ✅ Workflow errors → Global error handler
- ✅ Node failures → Comprehensive error logging
- ✅ Network issues → Retry mechanisms

## Performance Metrics

### **Industry Benchmarks Used**
- **CTR**: Good >2.0%, Average 1.5-2.0%, Poor <1.5%
- **CPC**: Good <€2.0, Average €2.0-3.0, Poor >€3.0
- **Conversion Rate**: Good >3%, Average 2-3%, Poor <2%
- **Impression Share**: Good >80%, Average 50-80%, Poor <50%

### **Analysis Contexts**
1. **Week-over-Week**: When previous week data is available
2. **Industry Benchmarks**: When historical data is missing
3. **Isolated Analysis**: For first-time campaigns

### **Access Control**
- Google Sheets integration with OAuth2
- Slack workspace-specific channels
- API key management through n8n credentials

## 📋 Setup Instructions

### **Prerequisites**
1. n8n instance (self-hosted or cloud)
2. Google Sheets with performance data
3. Slack workspace with designated channels
4. Google Gemini API access

### **Configuration Steps**
1. **Import Workflow**: Import the JSON file into n8n
2. **Configure Credentials**: Set up Google Sheets and Slack credentials
3. **Update Sheet IDs**: Replace Google Sheet document IDs
4. **Update Channel IDs**: Replace Slack channel IDs
5. **Test Workflow**: Add test data to Google Sheets
6. **Activate Workflow**: Enable the workflow for production

### **Required Permissions**
- **Google Sheets**: Read/Write access to performance data sheet
- **Slack**: Post messages to designated channels
- **Google Gemini**: API access for AI analysis

## 🧪 Testing

### **Test Scenarios**
1. **Valid Data Flow**: Add valid performance data
2. **Missing Previous Week**: Test with first week data
3. **Invalid Data**: Test with missing/invalid fields
4. **AI Failure**: Test with malformed AI output
5. **System Error**: Test error handling mechanisms

### **Expected Behaviors**
- ✅ Valid data → AI analysis → Appropriate notification
- ✅ Invalid data → Error notification → No processing
- ✅ AI failure → Retry → Fallback notification
- ✅ System error → Global error notification

## 📞 Support & Maintenance

### **Monitoring**
- Check Slack error channels regularly
- Monitor workflow execution logs
- Review AI analysis quality periodically
- Track notification accuracy

### **Troubleshooting**
- **Data Issues**: Check Google Sheets format and permissions
- **AI Issues**: Verify Gemini API credentials and quotas
- **Notification Issues**: Check Slack channel permissions
- **Workflow Issues**: Review n8n execution logs

### **Updates & Maintenance**
- Regular workflow performance reviews
- AI prompt optimization based on feedback
- Benchmark updates as industry standards change
- Error handling improvements based on real-world usage

## 🎯 Business Value

### **Immediate Benefits**
- **Automated Insights**: No manual analysis required
- **Proactive Alerts**: Early warning for performance issues
- **Consistent Reporting**: Standardized analysis format
- **Time Savings**: Automated weekly performance reviews

### **Long-term Value**
- **Performance Optimization**: Data-driven improvement recommendations
- **Cost Efficiency**: Reduced manual analysis overhead
- **Scalability**: Handles multiple campaigns and accounts
- **Reliability**: Robust error handling ensures continuous operation


---

**Built with ❤️ for automated performance optimization**
