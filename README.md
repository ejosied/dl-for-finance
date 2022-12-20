# dl-for-finance

## Deep Learning for Finance:
Using stock market news and daily close values to predict next-day stock increase or decrease

## Introduction

When imagining the applications of machine learning in the finance domain, many examples of tried-and-true methods come to mind—the nature of stock data lends itself nicely to time series forecasting, financial data in tabular form cooporates well with traditional regression and tree-based models, and text such as news articles can be used for semantic analysis. The multiple mediums of finance-realted data available inspired the idea to combine these approaches in a multi-phase model are compare it to the predictive performance of using just one medium.

Using Yahoo Finance data, two inputs—news articles and stock data—can be processed with their own LSTM sub-models, the outputs concatenated, and the result processed further with Dense layers to obtain a final prediction answering the question, "*Will the stock's close value increase or decrease the following day?*"

## Objectives

1) **Minimal goal**: Explore DNNs, RNNs, and LSTM approaches to predict decisions for one stock.

2) **Expected goal**: Extend the minimal goal by including text input from news sources, and develop a model to predict decisions for multiple stocks.

3) **Stretch goal**: Extend the expected goal by implementing scraping to obtain more diverse and more current text sources for stronger sentiment analysis.

I am pleased to say that I was able to fulfill the third version **stretch goal** of the project, including two methods of scraping to get the most complete news data from Yahoo Finance.

## Results

The model achieves about **53.4%** (reaching 54.2% at its peak) test observation-wise accuracy with early stopping, and **51.9%** test accuracy when considering the average prediction grouped by stock and publish date. By acquiring more data and continuing to experiment with hyperparameter tuning and model selection, these results may see substantial improvements. Limitations and ideas for future improvements are discussed in the final notebook, `models/multistage_model.ipynb`.

## Content

`edav/`
- `edav.ipynb`: A notebook of exploratory analysis and visualization of data available in the Yahoo Finance API.
- `grades_explained.png`: An image explaining the meaning of most grades present in the Yahoo Finance daata (source: https://www.investopedia.com/financial-edge/0512/understanding-analyst-ratings.aspx)

`preprocessing/`
- `scrape_news_yahoo_finance_api.ipynb`: Code to scrape news for stocks of interenst for URLs obtained directly from the Yahoo Finance API.
- `scrape_news_yahoo_finance_html.ipynb`: Code to scrape news from .txt files containing HTML code of Yahoo Finance Stock Market News search results.

`models/`
- `model_weights/`: A directory of weights saved from the trained model.
- `demo.ipynb`: A brief demo of model predictions and infrence with user interaction and visualized results.
- `multistage_model.ipynb/`: A notebook containing the code, explanations, and outcomes of the final model for this project.
- `stock_only_model.ipynb`: An experimental notebook focusing on time series stock data (modified from the TensorFlow tutorial on time series forecasting: https://www.tensorflow.org/tutorials/structured_data/time_series)
- `model.png`: A visualization of the final deep learning model.

Please note that **the data itself is not included in this respository** due to the large number of files. The notebooks in `preprocessing/` and `models/` expect data in the following file structure:

`data/`
- `htmls/*.txt`: Copied HTML code from Yahoo Finance Stock Market News search results.
- `scraped_news_from_api/*.csv`: All .csv files containing news scraped from URLs obtained through the Yahoo Finance API.
- `scraped_news_from_html/*.csv`: All .csv files containing news scraped from Yahoo Finance directly from HTML code.
