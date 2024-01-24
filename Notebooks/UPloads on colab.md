## Open In Colab Badge

  
Anybody can open a copy of any github-hosted notebook within Colab. To make it easier to give people access to live views of GitHub-hosted notebooks,

colab provides a [shields.io](http://shields.io/)-style badge, which appears as follows:

  

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb)

  

The markdown for the above badge is the following:

  

```markdown

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb)

```

  

The HTML equivalent is:

  

```HTML

<a href="https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb">

  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>

</a>

```

  

Remember to replace the notebook URL in this template with the notebook you want to link to.

## Saving Notebooks To GitHub or Drive

  

Any time you open a GitHub hosted notebook in Colab, it opens a new editable view of the notebook. You can run and modify the notebook without worrying about overwriting the source.

  

If you would like to save your changes from within Colab, you can use the File menu to save the modified notebook either to Google Drive or back to GitHub. Choose **File→Save a copy in Drive** or **File→Save a copy to GitHub** and follow the resulting prompts. To save a Colab notebook to GitHub requires giving Colab permission to push the commit to your repository.

### Save in as
```python
from google.colab import drive  
drive.mount('/content/drive')

%cd /content/drive/MyDrive/Github/
```
