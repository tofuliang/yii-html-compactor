yii-html-compactor
===================
The extension is a filter to compress the HTML output - to reduce bandwidth.
fork from http://www.yiiframework.com/extension/yii-html-compactor/       

The filter offers two compression methods:

###GZIP compression
Trim leading white space and blank lines from HTML output. But does not affect pre, script or textarea blocks.
Heads up: The GZIP compression is turned off for old buggy IE's (< IE7).

###Requirements 

Yii 1.1.10 or above...(could work with older versions)
tested with IE7-9, Firefox 13, Chromium, Safari 5.1
###Installation 

Extract the release file under protected/filters
put in a controller code blocks like the following...
###Usage 

##See the following code example:

###GZIP for all actions
```php
/**
     * @return array action filters
     */
    public function filters()
    {
        return array(
            array(
                'application.filters.html.ECompressHtmlFilter',
                'gzip'            => (YII_DEBUG ? false : true),
                'doStripNewlines' => (YII_DEBUG ? false : true),
                'actions' => '*'
            ),
        );
    }
```
###GZIP only for index & admin action in controller with CRUD actions
```php
/**
     * @return array action filters
     */
    public function filters()
    {
        return array(
            array(
                'application.filters.html.ECompressHtmlFilter',
                'gzip'            => (YII_DEBUG ? false : true),
                'doStripNewlines' => (YII_DEBUG ? false : true),
                'actions' => 'index, admin'
            ),
        );
    }
```
###Trim leading white space, blank lines & new lines from HTML output for all action
```php
/**
     * @return array action filters
     */
    public function filters()
    {
        return array(
            array(
                'application.filters.html.ECompressHtmlFilter',
                'gzip'    => false,
                'actions' => 'ALL'
            ),
        );
    }
```
###Nothing will compressed
```php
/**
     * @return array action filters
     */
    public function filters()
    {
        return array(
            array(
                'application.filters.html.ECompressHtmlFilter',
            ),
        );
    }
```