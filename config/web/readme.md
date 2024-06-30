# Web Scraping Configurations Guide

This readme provides a clear explanation of the code examples included in this project. Their purpose is to demonstrate how to extract information from various sections of the Lisbon School of Engineering's website (https://www.isel.pt/) and how to properly structure the configurations for the web scraper.

## Table of Contents

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [**Understanding the Code**](#understanding-the-code)
- [**Entries**](#entries)
- [**Selectors**](#selectors)
- [**Actions**](#actions)
- [**Attributes**](#attributes)
- [**Examples**](#examples)
    * [**Example 1: Extracting News Article Titles**](#example-1-extracting-news-article-titles)
        + [**Explanation**](#explanation)
        + [**Output**](#output-outputnews_20240501_131318json)
    * [**Example 2: Extracting News Article Title and Links**](#example-2-extracting-news-article-title-and-links)
        + [**Explanation**](#explanation-1)
        + [**Output**](#output-outputnews_20240501_131844json)
- [**What is .json?**](#what-is-json)
    * [**Storing JSON**](#storing-json)
    * [**Naming JSON Files**](#naming-json-files)

<!-- TOC end -->


<!-- TOC --><!--suppress HtmlDeprecatedAttribute -->
<a name="understanding-the-code"></a>
## **Understanding the Code**

The code snippets you see are structured configurations that instruct a web scraper on how to fetch and organize data from websites. Let's break down the key components:

<!-- TOC --><a name="entries"></a>
## **Entries**

Each entry in this context represents a distinct task for the web scraper. It is characterized by a starting point (`url`) and a set of directives (`children`) to execute on that particular webpage.

But wait, there's more! We've also integrated `pagination` into the entries. This functionality enables the scraper to traverse through numerous pages of results seamlessly. Additionally, you can customize the output file using `output_dir` and `output_name` parameters.


<!-- TOC --><a name="selectors"></a>
## **Selectors**
Selectors are like treasure maps; they guide the scraper to the specific pieces of information you want. These use CSS selectors, a powerful way to pinpoint elements on a web page. If you're new to CSS selectors, refer to this fantastic documentation [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors).

<!-- TOC --><a name="actions"></a>
## **Actions**
The different `action` values tell the scraper what to do:
* `entry`: Represents the starting point of the scraping process.
* `navigate`: Tells the scraper to follow a link and do more tasks there.
* `select`: Allows the scraper to select specific groups of elements based on the `selector` provided.
* `extract`: Tells the scraper to extract information from the selected elements. We have two types of extractors and to use them we have to specify the `type`:
    * `item`: Extracts a single piece of information (like text or an attribute).
    * `list`: Extracts multiple pieces of information as a list.

Here's a snippet to illustrate how actions are used:

```json
[
  {
    "action": "entry"
  },
  {
    "action": "navigate"
  },
  {
    "action": "select"
  },
  {
    "action": "extract",
    "type": "item"
  },
  {
    "action": "extract",
    "type": "list"
  }
]
```

<!-- TOC --><a name="attributes"></a>
## **Attributes**
These are some examples that define what kind of data the scraper should collect, we call them `attributes`:

* `text`: Extract the text content of an element.
* `href`: Extract the URL from a link.
* `src`: Extract the source URL of an image.
* `alt`: Extract the 'alt text' of an image (useful for accessibility).
* `datetime`: Extract a date-time value.

More attributes can be used depending on the data you want to extract. You should definitely check the documentation [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes).

<!-- TOC --><a name="examples"></a>
## **Examples**

Let's look at one example to see how it all fits together:

<!-- TOC --><a name="example-1-extracting-news-article-titles"></a>
### **Example 1: Extracting News Article Titles**
```json  
[
  {
    "action": "entry",
    "url": "[https://www.isel.pt/noticias](https://www.isel.pt/noticias)",
    "output_dir": "output",
    "output_name": "news",
    "children": [
      {
        "action": "select",
        "selector": ".item-columns",
        "children": [
          {
            "action": "extract",
            "type": "item",
            "selector": ".views-field-title a",
            "attribute": "text",
            "key": "title"
          }
        ]
      }
    ]
  }
]
```

<!-- TOC --><a name="explanation"></a>
#### **Explanation**

1. **Entry Point:** The scraper will start at https://www.isel.pt/noticias (the 'News' section).
2. **Selection:** It locates elements with the CSS class `.item-columns` (likely news article containers).
3. **Extraction:** From each news item, it finds:
    - The news article's title (from the `.views-field-title` a element, saving the text content with the key `title`).
4. **Output:** The extracted titles will be saved in the `output/news_<timestamp>.json` file.

<!-- TOC --><a name="output-outputnews_20240501_131318json"></a>
#### **Output**:
The output file (`output/news_20240501_131318.json`) resulted in a JSON file with the following structure:
```json
[
  {
    "title": "ISEL dinamiza BIP sobre sustentabilidade ambiental"
  },
  {
    "title": "Royal Society of Chemistry distingue professor João Gomes"
  },
  {
    "title": "ISEL recebeu o Encontro Nacional das Agências de Energia e Ambiente 2024"
  },
  {
    "title": "Tomada de posse de membros do Conselho de Representantes do ISEL"
  },
  {
    "title": "Rothoblaas estreia-se no ISEL"
  },
  {
    "title": "Elisabete Alegria é editora do livro \"Catalysis for a Sustainable Environment: Reactions, Processes and Applied Technologies\""
  }
]
```

This example showcases how the scraper can be configured to extract specific information, in this case, the titles of news articles.

Let's delve into one more example tailored to the website:

<!-- TOC --><a name="example-2-extracting-news-article-title-and-links"></a>
### **Example 2: Extracting News Article Title and Links**

We can enhance the previous example by extracting both the titles and URLs of news articles. Here's how we can achieve that:

```json
[
  {
    "action": "entry",
    "url": "https://www.isel.pt/noticias",
    "output_dir": "output",
    "output_name": "news",
    "children": [
      {
        "action": "select",
        "selector": ".item-columns",
        "children": [
          {
            "action": "extract",
            "type": "item",
            "selector": ".views-field-title a",
            "attribute": "text",
            "key": "title"
          },
          {
            "action": "extract",
            "type": "item",
            "selector": ".views-field-title a",
            "attribute": "href",
            "key": "url"
          }
        ]
      }
    ]
  }
]
```

<!-- TOC --><a name="explanation-1"></a>
#### **Explanation**

1. **Entry Point:** The scraper will start at https://www.isel.pt/noticias (the 'News' section).
2. **Selection:** It locates elements with the CSS class `.item-columns` (likely news article containers).
3. **Extraction:** From each news item, it finds:
    - The news article's title (from the `.views-field-title` a element, saving the text content with the key `title`).
    - The URL of the news article (from the `.views-field-title` a element, saving the URL with the key `url`).
4. **Output:** The extracted titles and URLs will be saved in the `output/news_<timestamp>.json` file.

This example demonstrates how the scraper can be configured to extract as much information as needed, in this case, the URLs of news articles.

<!-- TOC --><a name="output-outputnews_20240501_131844json"></a>
#### **Output**

The output file (`output/news_20240501_131844.json`) resulted in a JSON file with the following structure:
```json
[
  {
    "title": "ISEL dinamiza BIP sobre sustentabilidade ambiental",
    "url": "/noticias/isel-dinamiza-bip-sobre-sustentabilidade-ambiental"
  },
  {
    "title": "Royal Society of Chemistry distingue professor João Gomes",
    "url": "/noticias/royal-society-chemistry-distingue-professor-joao-gomes"
  },
  {
    "title": "ISEL recebeu o Encontro Nacional das Agências de Energia e Ambiente 2024",
    "url": "/noticias/isel-recebeu-o-encontro-nacional-das-agencias-de-energia-e-ambiente-2024"
  },
  {
    "title": "Tomada de posse de membros do Conselho de Representantes do ISEL",
    "url": "/noticias/tomada-de-posse-de-membros-do-conselho-de-representantes-do-isel"
  },
  {
    "title": "Rothoblaas estreia-se no ISEL",
    "url": "/noticias/rothoblaas-estreia-se-no-isel"
  },
  {
    "title": "Elisabete Alegria é editora do livro \"Catalysis for a Sustainable Environment: Reactions, Processes and Applied Technologies\"",
    "url": "/noticias/elisabete-alegria-e-editora-do-livro-catalysis-sustainable-environment-reactions-processes"
  }
]
```

<!-- TOC --><a name="what-is-json"></a>
## **What is .json?**

With all the examples using `.json` files, you might be wondering what they are. Here's a brief overview:

- JSON (JavaScript Object Notation) is a standard, lightweight format for storing and exchanging data.
- It's a text-based format that uses a human-readable structure of key-value pairs to represent information.
- JSON is ideal for configuration data because it's easy for both humans and computers to understand.

You can learn more about JSON [here](https://www.json.org/json-en.html).

<!-- TOC --><a name="storing-json"></a>
### **Storing JSON**

- You can store JSON data in a `.json` file, which is a text file with the `.json` extension.
- JSON files are easy to read and write, making them a popular choice for configuration files.
- JSON files can be opened and edited with any text editor, but you can also use specialized JSON editors for a better experience.

<!-- TOC --><a name="naming-json-files"></a>
### **Naming JSON Files**

- The names are descriptive and should reflect the purpose of the data they contain.
- It's a good practice to use lowercase letters and separate words with hyphens or underscores.
- The `.json` extension indicates that the file contains JSON data.
- Examples:
    - `config_bachelors.json`: Contains configuration data for scraping bachelor's degree programs.
    - `config_events.json`: Contains configuration data for scraping events.

<br />
<div style="text-align: center;">Made with ❤️ by <a href="mailto:a49761@alunos.isel.pt">Rafael Guilherme</a> & <a href="mailto:a49758@alunos.isel.pt">Francisco Rodrigues</a></div>
