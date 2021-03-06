---
published: true
layout: post
excerpt: description
categories: articles
share: true
tags:
  - python
  - virtualization
---
# 1.Check taht venv is installed
```shell 
python -m venv
```

If it isn't install it 
```shell
pip install --user virtualenv
```

# 2.Create your virtual env
```shell
python -m venv  [project name] 
```

If you get the following error 

```shell
Error: Command ... -Im, ensurepip, --upgrade, --default-pip returned non-zero exit status 1.
```

Exclude pip from your environment and install it separately : [More info](https://stackoverflow.com/questions/26215790/venv-doesnt-create-activate-script-python3)

```shell
python -m venv --without-pip [project name] 

source [project name]/bin/activate
curl https://bootstrap.pypa.io/get-pip.py | python   
deactivate
source [project name]/bin/activate
```

# 3. Activate your environment
```shell
source [env]/bin/activate
```

Check that your python is now the one that is in your environment

```shell
which python
```

# 4. Deactivate your environment
```shell
deactivate
```

