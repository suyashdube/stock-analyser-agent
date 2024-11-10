# stock-analyser-agent
a multi-agent system for analyzing stock performance and identifying the best-performing stocks over a 3-month period. 

Initialization:
- necessary libraries include yfinance, numpy, datetime, concurrent.futures, transformers
- Using GPT-Neo model pipeline for text generation (LLM-powered agent).

  
LLM Search Agent (llm_search_agent):
- Uses the GPT-Neo model to generate a response based on a given instruction.

  
Stock Performance Fetching agent:
- fetch_stock_performance: Fetches 3-month performance data for a single stock.
- fetch_top_10_stocks: Uses ThreadPoolExecutor to parallelize fetching data for multiple stocks and identifies the top 10 performers.

  
Data Fetching and Normalization:
- data_fetcher: Retrieves historical price data for a given stock ticker.
- normalize_prices: Normalizes the price data to percentage changes from the initial price.

  
Performance Analysis agent (performance_analyzer):
- Analyzes the normalized price data for each stock.
- Calculates average returns and identifies the best-performing stock.

  
Main Execution Flow (main function):
- using the LLM agent to interpret the task.
- Fetches the top 10 performing stocks.
- Retrieves and normalizes price data for these stocks.
- Analyzes performance to identify the best-performing stock.

  
Execution:
- The script runs the main function when executed directly.

  
Methodologies:
- Using yfinance for real-time stock data retrieval.
- Implementing parallel processing for faster data fetching.
- Incorporating LLM-based interpretation using GPT-Neo model from huggingface.
- Performing data normalization and analysis to identify top-performing stocks.
The project demonstrates the concept of using multiple specialized agents (LLM, data fetching, analysis) working together to accomplish a complex task.

Code flow diagram:

                                 +------------------------+
                                 |     Main Execution     |
                                 +------------------------+
                                             |
                                             v
                 +--------------------------------------------------+
                 |                  LLM Search Agent                |
                 | (Interprets instruction using GPT-Neo model)     |
                 +--------------------------------------------------+
                                             |
                                             v
                 +--------------------------------------------------+
                 |           Stock Performance Fetching             |
                 |                                                  |
                 |  +-------------------------------------------+   |
                 |  |           fetch_top_10_stocks()           |   |
                 |  |                                           |   |
                 |  |  +-------------------------------------+  |   |
                 |  |  |      ThreadPoolExecutor            |  |   |
                 |  |  |  +-----------------------------+   |  |   |
                 |  |  |  | fetch_stock_performance()  |   |  |   |
                 |  |  |  | (for multiple stocks)      |   |  |   |
                 |  |  |  +-----------------------------+   |  |   |
                 |  |  +-------------------------------------+  |   |
                 |  +-------------------------------------------+   |
                 +--------------------------------------------------+
                                             |
                                             v
                 +--------------------------------------------------+
                 |              Data Fetching & Normalization       |
                 |                                                  |
                 |  +-------------------------------------------+   |
                 |  |             data_fetcher()                |   |
                 |  | (Retrieves historical data for each stock)|   |
                 |  +-------------------------------------------+   |
                 |                        |                         |
                 |                        v                         |
                 |  +-------------------------------------------+   |
                 |  |           normalize_prices()              |   |
                 |  | (Calculates percentage change from start) |   |
                 |  +-------------------------------------------+   |
                 +--------------------------------------------------+
                                             |
                                             v
                 +--------------------------------------------------+
                 |              Performance Analysis                |
                 |                                                  |
                 |  +-------------------------------------------+   |
                 |  |         performance_analyzer()            |   |
                 |  | (Identifies best performing stock)        |   |
                 |  +-------------------------------------------+   |
                 +--------------------------------------------------+
                                             |
                                             v
                 +--------------------------------------------------+
                 |                 Results Output                   |
                 | (Prints best performing stock and its return)    |
                 +--------------------------------------------------+
