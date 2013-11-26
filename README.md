# TRANSCODE Blog

Built on [Jekyll Incorporated](http://blog.sendtoinc.com)

## Installation & Usage

    bundle install
    rake setup
    jekyll serve --watch

## Configuration

Edit: _config.yml (general options), main.css (theme colors &amp; fonts)

```
_config.yml
_assets/
    ├── stylesheets/
        ├── main.scss
```

_Note: when editing _config.yml, you need to restart jekyll to see the changes.__

    
## Publish to Github Pages

1. Add your domain to _CNAME_
2. Edit your repo address at _Rakefile_
    
Run rake task. **NOTE: It will deploy the generated site to _gh-pages_ branch overwriting it**    
``` 
rake site:publish
```

## Copyright and license

Jekyll Incorporated, Copyright 2013 Kippt Inc. under [The MIT License ](LICENSE)


