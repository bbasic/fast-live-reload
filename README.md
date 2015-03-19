# fast-live-reload
A live reload that works with all the possible browsers (ie8+)
without external dependencies (like jQuery), and can also serve
local files.

## Why

I wanted a tool where I can test small and bigger applications with
ease on different browsers, even on remote machines (see for example
[https://www.modern.ie/en-us]() ).

This tool is specifically designed for that.

## Example
```
$ fast-live-reload
Serving . on port 9000
Changes are served on port: 9001
Monitoring paths: '.' every 100 millis.
```

This will start monitoring the current folder for changes,
serving it on port 9000, and using port 9001 in order to notify
updates. All of the above parameters can be changed.

Make sure the `client-fast-reload.js` is
loaded into your application (see **Install** section for details):

```html
<!-- remove in production!! -->
<script type="text/javascript" src="client-fast-reload.js"></script>
```

## A More Advanced Example

```sh
fast-live-reload -s /tmp -p 8000 path1 path2 path3
```

This will monitor the given paths: `path1`, `path2` and `path3`, serve the `/tmp` folder
on port `9000`, and publishing the changes on port `8000`.

### Different Port Configuration

Since the port is different, this also needs to reflect in the client.
There are several ways to configure this.

#### 1. fastLiveReloadHost Global Variable

Use the global variable `fastLiveReloadHost`.

```html
<!-- remove in production!! -->
<script type="text/javascript">
    window.fastLiveReloadHost="localhost:8000";
</script>
<script type="text/javascript" src="client-fast-reload.js"></script>
```

#### 2. fastLiveReloadHost Query Parameter

In the URL of the page that includes the `client-fast-reload.js` script,
add the `fastLiveReloadHost` query parameter.

For example:
```
http://my-site:1111/my-site/my-page.jsp?fastLiveReloadHost=localhost:8000
```

You can still use other parameters if you wish. This will overwrite the
`fastLiveReloadHost` global variable setting if it is defined.

#### 3. fastLiveReloadHost Hash Parameter

*This option is preferred*

In the URL of the page that includes the `client-fast-reload.js` script,
add the `fastLiveReloadHost` query parameter.

For example:
```
http://my-site:1111/my-site/my-page.jsp#fastLiveReloadHost=localhost:8000
```

This has the highest precedence, and will overwrite other settings.

## Install

In order to install this run:

```sh
npm install -g fast-live-reload
```

To fetch the client javascript, run:

```sh
bower install fast-live-reload
```

If you don't have yet bower installed, of course, install it first:
```sh
npm install -g bower
```

## Change Log

* v1.0.0  2015-03-19  Initial Release

