# Static Website

This project will demonstrate creating a new Rails project. This tutorial will give an overview of the Rails directory structure.  It will also give insight on how to serve static web pages and associated assets within a Rails project. 

These techniques are used daily in creating marketing or other static content.

```
# create a new rails project
$ rails new tutorial
```

[[/section2/static_img01.png]]


```
$ cd tutorial
```

[[/section2/static_img02.png]]


```
# start the server
$ rails s
```

[[/section2/static_img03.png]]

Open your web browser. Go to http://localhost:3000

[[/section2/static_img04.png]]


Open your preferred editor and create an HTML page. Save it and name it helloworld.html. Place the page in the public directory.

```html

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Tutorial Static Page</title>
</head>
<body>

<!-- place static pages within RAILS_ROOT/public -->

Hello World!

</body>
</html>

```

Open a web browser window. Go to 

[[http://localhost:3000/helloworld.html]]


