##### About
This project includes:

* [slimit 0.7.4(modified by emptyhua to be Python 2.4 compatible)](http://pypi.python.org/pypi/slimit)
* [ply 3.4](http://www.dabeaz.com/ply/) 
* [odict 1.5.0](http://pypi.python.org/pypi/odict/)
* [rcssmin 1.0.0](http://opensource.perlig.de/rcssmin/)

##### Requirements:
Python &gt;= 2.4

##### Usage:
###### css minify
    #!/usr/bin/env python

    import urllib
    from rcssmin import cssmin

    css_content = urllib.urlopen('http://static.jquery.com/files/rocker/css/screen.css').read()
    print cssmin(css_content)

###### js minify
    #!/usr/bin/env python

    import urllib
    from slimit import minify as jsminify

    js_content = urllib.urlopen('http://code.jquery.com/jquery-1.8.1.js').read()
    print jsminify(js_content, mangle=True, mangle_toplevel=False)

#### Benchmark
    $ls ./jquery*
    #raw
    256K jquery-1.8.1.js
    #download from jquery.com
     92K jquery-1.8.1.min.js
     36K jquery-1.8.1.min.js.gz
    #http://closure-compiler.appspot.com
     84K jquery-1.8.1.google.advanced.js
     32K jquery-1.8.1.google.advanced.js.gz
     92K jquery-1.8.1.google.simple.js
     36K jquery-1.8.1.google.simple.js.gz
    #http://dean.edwards.name/packer
    120K jquery-1.8.1.packer.js
     40K jquery-1.8.1.packer.js.gz
    #http://refresh-sf.com/yui
    #Uncaught SyntaxError: Unexpected token } 
     64K jquery-1.8.1.yui.js
     24K jquery-1.8.1.yui.js.gz
    #slimit
     96K jquery-1.8.1.slimit.js
     36K jquery-1.8.1.slimit.js.gz

