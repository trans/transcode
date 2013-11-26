# TRANSCODE Blog

Built on [Jekyll Incorporated](http://blog.sendtoinc.com)

## Usage

After an initial clone run one time only:

    rake setup

This will run `bundle install` and will clone the wiki to `_wiki`.

After editing posts or other files run as needed:

    rake generate

To publish the site run:

    rake publish


## Configuration

Edit _config.yml (general options) and main.css (theme colors &amp; fonts)

```
_config.yml
_assets/
    ├── stylesheets/
        ├── main.scss
```

_Note: when editing _config.yml, you need to restart jekyll to see the changes.__


## NOTES
    
Add domain to _CNAME_ if ever needed.


## Copyright and license

TRANSCODE, Copyright (cc) 2013 trans

Jekyll Incorporated, Copyright 2013 Kippt Inc. under [The MIT License ](LICENSE)


