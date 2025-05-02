## ✨ Description
A real-time n8n workflow that aggregates cryptocurrency sentiment from multiple sources (Santiment APIs: twitter, reddit, telegram, bitcointalk, youtube; Tavily web scraping) and uses GPT-4o 🧠 to analyze the data, outputting concise JSON insights 📊.

## 🛠️ Workflow Steps

1. **⚡ Manual Trigger**: Start the workflow.
2. **🤖 AI Agent**: Chooses which sentiment tools to run based on coin type.
3. **🌐 Tavily Fetch**: Scrape news and social mentions.
4. **📈 Sentiment Nodes**: Retrieve weighted sentiment metrics from Santiment for each platform.
5. **✅ Output Parser**: Format and validate the final JSON with keys:

   * `confidence` (0.0–1.0) 🔒
   * `reasoning` (brief explanation) 📝
   * `used_tools` (tools consulted) 🧰
   * `santiment` (per-source metrics) 📋

## ⚙️ Setup & Configuration

1. **📥 Download & Clone Repository**

````bash
git clone https://github.com/dharmeshdarshan08/Sentiment-Aggregator-AI-Analyzer-for-Crypto.git
cd Sentiment-Aggregator-AI-Analyzer-for-Crypto
````

2. **🐳 Install & Run n8n**

   * **Docker**:

     ```bash
     docker run -it --rm \
       --name n8n \
       -p 5678:5678 \
       -v ~/.n8n:/home/node/.n8n \
       n8nio/n8n
     ```
   * **Local**:

     ```bash
     npm install -g n8n
     n8n start
     ```
3. **🔑 Login to n8n Editor**
   * Enter your n8n credentials (or complete initial setup)
     
4. **📂 Import Workflow**
   * Click **Import** → **From File**
   * Select `Http_as_tool.json`
   * The **Http as tool** workflow appears in your list
     
5. **🔐 Configure Credentials**

   1. **OpenAI**
      * **Credentials** → **New Credential** → **OpenAI API**
      * Name: `OpenAI GPT-4o`
      * Paste your GPT-4o API key 🔑
        
   2. **Santiment**
      * In each sentiment HTTP Request node, add header `Apikey`: `<YOUR_SANTIMENT_KEY>`
        
   3. **Tavily**
      * In `fetch_data_from_tavily` node **Headers**:
        * `Content-Type`: `application/json`
        * `Authorization`: `tvly-dev-...` 🛡️
          
6. **✅ Activate & Test**

   * Toggle the workflow switch to **Active**
   * Select **Http as tool** and click **Execute Workflow**
   * Check JSON insights in **Structured Output Parser**

## 🚀 Usage

* 🚀 **Run Workflow**: In n8n, select **Http as Tool** and click **Execute Workflow**.
* 🔍 **Review Output**: Inspect the final JSON output in the **Structured Output Parser** node.

## 🔧 Customization

* **Coin Slug & Time Range**: Edit prompts or query parameters.
* **Add/Remove Platforms**: Duplicate or remove HTTP Request nodes.

