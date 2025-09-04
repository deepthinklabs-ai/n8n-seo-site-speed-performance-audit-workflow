# SEO Site Speed/Performance Review n8n Workflow

Automated SEO site speed and performance review workflow using n8n, PageSpeed Insights API, Chrome UX Report, and Claude AI for comprehensive performance analysis and recommendations.

## 🎯 Overview

This n8n workflow provides comprehensive performance analysis of websites by:

- **Discovering pages** via sitemap parsing or fallback crawling
- **Analyzing performance** using Google PageSpeed Insights API (mobile & desktop)
- **Collecting real-user data** from Chrome User Experience Report (CrUX)
- **Generating insights** with Claude AI for actionable recommendations
- **Delivering reports** via email with prioritized fixes

## ✨ Features

### Smart Page Discovery
- Fetches and parses XML sitemaps (including sitemap index files)
- Handles child sitemaps for comprehensive coverage
- Fallback HTML crawling when sitemaps aren't available
- Intelligent filtering of non-HTML resources

### Performance Analysis
- **Lab Data**: Core Web Vitals (LCP, CLS, INP), TTFB, FCP, TTI, TBT
- **Field Data**: Real user metrics from Chrome UX Report
- **Resource Analysis**: Transfer sizes, image optimization, JS/CSS metrics
- **Opportunities**: Render-blocking resources, unused code, image optimization

### AI-Powered Insights
- Claude AI analyzes performance data
- Generates prioritized recommendations (P0/P1/P2)
- Provides specific, actionable guidance
- Focuses on Core Web Vitals thresholds and modern best practices

### Reporting
- Professional email reports with findings and recommendations
- Clear performance scores and metrics
- Actionable next steps for optimization

## 🛠️ Setup

### Prerequisites

1. **n8n instance** (cloud or self-hosted)
2. **Google Cloud API key** with PageSpeed Insights API enabled
3. **Anthropic API key** for Claude AI
4. **SMTP credentials** for email delivery

### API Setup

#### Google PageSpeed Insights API
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing
3. Enable PageSpeed Insights API
4. Create API key and restrict to PageSpeed Insights API
5. Add the API key to n8n credentials

#### Anthropic Claude API
1. Sign up at [Anthropic](https://console.anthropic.com/)
2. Generate API key
3. Add to n8n Anthropic credentials

### Installation

1. **Import the workflow**:
   - Download `workflow.json` from this repository
   - In n8n, go to Workflows → Import from file
   - Select the downloaded JSON file

2. **Configure credentials**:
   - **Query Auth**: Add your Google API key
   - **Anthropic API**: Add your Claude API key  
   - **SMTP**: Configure email credentials

3. **Update configuration**:
   - Modify the "Init Site" node with your target website
   - Update email addresses in the "Send email" node

## 🚀 Usage

### Basic Usage

1. **Set target website**: Update the `site` variable in the "Init Site" node
2. **Execute workflow**: Click "Execute workflow" to start the analysis
3. **Monitor progress**: Watch as the workflow discovers pages and analyzes performance
4. **Receive report**: Get comprehensive performance report via email

### Customization

#### Adjust Analysis Scope
- Modify sitemap parsing logic to focus on specific sections
- Adjust the page limit in URL expansion nodes
- Filter specific page types or paths

#### Customize Reports
- Update the Claude AI prompt for different analysis focus
- Modify email template and styling
- Add additional recipients or notification channels

#### Performance Thresholds
- Adjust Core Web Vitals thresholds in the analysis code
- Customize scoring algorithms
- Modify priority levels for recommendations

## 📊 Workflow Architecture

### Main Components

1. **Page Discovery Pipeline**
   - Sitemap fetching and parsing
   - Child sitemap processing
   - Fallback HTML crawling

2. **Performance Analysis Pipeline**
   - PageSpeed Insights API calls (mobile & desktop)
   - Chrome UX Report data collection
   - Data extraction and normalization

3. **AI Analysis & Reporting**
   - Claude AI performance evaluation
   - Report generation and formatting
   - Email delivery

### Data Flow

```
Website URL → Sitemap Discovery → Page URLs → Performance Analysis → AI Analysis → Email Report
```

## 🔧 Technical Details

### APIs Used
- **PageSpeed Insights API v5**: Lab and field performance data
- **Chrome UX Report API**: Real user experience metrics
- **Anthropic Claude API**: AI-powered analysis and recommendations

### Core Web Vitals Thresholds
- **LCP (Largest Contentful Paint)**: ≤ 2.5s (good), ≤ 4.0s (needs improvement)
- **CLS (Cumulative Layout Shift)**: ≤ 0.1 (good), ≤ 0.25 (needs improvement)  
- **INP (Interaction to Next Paint)**: ≤ 200ms (good), ≤ 500ms (needs improvement)

### Performance Categories
- **P0 (Critical)**: Issues significantly impacting Core Web Vitals
- **P1 (High)**: Important optimizations with measurable impact
- **P2 (Medium)**: Additional improvements for optimization

## 📈 Sample Output

The workflow generates detailed reports including:

- **Performance Scores**: 0-100 rating for mobile and desktop
- **Core Web Vitals Status**: Pass/fail for LCP, CLS, INP
- **Key Findings**: Specific performance issues identified
- **Prioritized Recommendations**: Actionable fixes organized by priority
- **Technical Details**: Resource sizes, blocking resources, optimization opportunities

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- Additional performance metrics and analysis
- Enhanced reporting formats (PDF, dashboard integration)
- Integration with other SEO tools and APIs
- Performance tracking over time
- Batch processing for multiple websites

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙋‍♂️ Support

For questions and support:
- email dave@deepthinklabs.ai - Happy to help!
- Create an issue in this repository
- Check the [n8n documentation](https://docs.n8n.io/)
- Review the [PageSpeed Insights API documentation](https://developers.google.com/speed/docs/insights/v5/get-started)

---

**Built with ❤️ using n8n, Google PageSpeed Insights, Chrome UX Report, and Claude AI**
