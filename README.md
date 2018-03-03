# TCLB_docs

This short tutorial will show you how to serve the webpage at you local machine at test your changes.

First, it is safe to isolate your enviroment.

Install virtual enviroment:
```sh
$ pip3 install virtualenv virtualenvwrapper
$ source /usr/local/binyy/virtualenvwrapper.sh
```

You can lookup your pythons' distributions using `$ whereis python` or just pick the default one...

```sh
$ mkvirtualenv --python=$(which python3) tclb-docs-env
```

To activate `$ workon tclb-docs-env`, to deactive enter `$ deactivate`

Install dependencies:
```sh
(tclb-docs-env) $  pip install -r requirements.txt
```

Run server on you local machine:
```sh
(tclb-docs-env) $ mkdocs serve
```

#### Common issues

It may be required to run: 
$ apt-get install python3.6-dev
