# Develop and sell a Python API. From start to end tutorial.

[<img src="XXXXXXXX">](
httpsasdfafasfasfdasf)
xxxxxxx - httpsasdfafasfasfdasf

![https://unsplash.com/photos/LJ9KY8pIH3E](https://images.unsplash.com/photo-1534972195531-d756b9bfa9f2?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80)


I recently read a blog post about setting up your own API and selling it.

I was quite inspired and wanted to test if it works. In just 5 days I was able to create a product from start to end. So I thought I share issues I came across, elaborate on concepts that the article was introducing, and provide a quick checklist to build something yourself.



## Table of Contents

- [Develop and sell a Python API. From start to end tutorial.](#develop-and-sell-a-python-api-from-start-to-end-tutorial)
  - [Table of Contents](#table-of-contents)
  - [Stack used](#stack-used)
  - [1. Create project formalities](#1-create-project-formalities)
  - [2. Create a solution for a problem](#2-create-a-solution-for-a-problem)
    - [Install packagees](#install-packagees)
    - [Develop solution to problem](#develop-solution-to-problem)
      - [Download data](#download-data)
      - [Create functionality](#create-functionality)
    - [Build server to execute function with REST](#build-server-to-execute-function-with-rest)
  - [Set up zappa](#set-up-zappa)
  - [Inspiration](#inspiration)
  - [About](#about)

## Stack used

We will use

- Github (Code hosting),
- Anaconda (Dependency and environment management),
- Jupyter Notebook (code development and documentaion),
- Python (programming language),
- AWS (deployment),
- RapidAPI (market to sell)

## 1. Create project formalities

This is always an annoying step. It's always the same but necessary.

1. Create local folder `mkdir NAME`
2. Create new repository on Github with `NAME`
3. Create conda environment `conda create --name NAME python=3.7`
4. Activate conda environment `conda activate PATH_TO_ENVIRONMENT`
5. Create git repo `git init`
6. Connect to Github repo. Add Readme file, commit it and
```sh
git remote add origin URL_TO_GIT_REPO
git push -u origin master
```

Now we have:
- [x] local folder
- [x] github repository
- [x] anaconda virtual environment
- [x] git version control


## 2. Create a solution for a problem

### Install packagees

Install jupyter notebook and jupytext:

```sh
pip install notebook jupytext
```

sets a hook in  `.git/hooks/pre-commit` for tracking the notebook changes in git properly:

```sh
#!/bin/sh

jupytext --from ipynb --to jupytext_conversion//py:light --pre-commit
```

### Develop solution to problem

```sh
pip install pandas requests
```

Add a `.gitignore` file and add the data folder (`data/`) to not upload the data to the hosting.

#### Download data

Download an example dataset (titanic dataset) and save it into a data folder:

```py
def download(url: str, dest_folder: str):
    if not os.path.exists(dest_folder):
        os.makedirs(dest_folder)

    filename = url.split('/')[-1].replace(" ", "_")
    file_path = os.path.join(dest_folder, filename)

    r = requests.get(url, stream=True)
    if r.ok:
        print("saving to", os.path.abspath(file_path))
        with open(file_path, 'wb') as f:
            for chunk in r.iter_content(chunk_size=1024 * 8):
                if chunk:
                    f.write(chunk)
                    f.flush()
                    os.fsync(f.fileno())
    else:
        print("Download failed: status code {}\n{}".format(r.status_code, r.text))


url_to_titanic_data = 'https://web.stanford.edu/class/archive/cs/cs109/cs109.1166/stuff/titanic.csv'

download(url_to_titanic_data,'./data')
```

#### Create functionality

Transform format

```py
df = pd.read_csv('./data/titanic.csv')
df.to_json(r'./data/titanic.json')
```

### Build server to execute function with REST




Now we have the functionality to transform csv files into json for example.

## Set up zappa



## Inspiration

The article ["API as a product. How to sell your work when all you know is a back-end"](https://towardsdatascience.com/api-as-a-product-how-to-sell-your-work-when-all-you-know-is-a-back-end-bd78b1449119) by Artem provided a great idea, namely to

> - Make an API that solves a problem
> - Deploy it with a serverless architecture
> - Distribute through an API Marketplace

I encourage you to have a look at his article.





---

## About

Daniel is an entrepreneur, software developer and lawyer. He has worked at various IT companies, tax advisory, management consulting and at the Austrian court.

His knowledge and interests currently revolve around programming machine learning applications and all its related aspects. To the core, he considers himself a problem solver of complex environments, which is reflected in his various projects.

Don't hesitate to get in touch if you have ideas, projects, or problems.

![picture of myself](https://avatars2.githubusercontent.com/u/22077628?s=460&v=4)

**Connect on:**
- [LinkedIn](https://www.linkedin.com/in/createdd)
- [Github](https://github.com/Createdd)
- [Medium](https://medium.com/@createdd)
- [Twitter](https://twitter.com/_createdd)
- [Instagram](https://www.instagram.com/create.dd/)


<!-- Written by Daniel Deutsch -->