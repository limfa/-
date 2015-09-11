# CSS公共样式重置

```scss
*{
    padding: 0;
    margin: 0;
    font: inherit;
    color: inherit;
}
body{
    color: #000;
    background-color: #fff;
    // in chrome ,the min line-height of <input> is 1.4em * 14px;why ? i do't know
    font: normal 14px/1.4em "microsoft yahei", tahoma, arial ;
}
iframe {
    border: none;
}
input, button {
    outline: none;
    border: 0;
}
input[type=submit], input[type=button], input[type=checkbox], input[type=radio], button {
    cursor: pointer;
}
ul, ol {
    list-style: none;
}
img {
    border: 0;
    vertical-align: middle;
}
table {
    border-collapse: collapse;
    border-spacing: 0;
}
td, th {
    padding: 0;
}
a {
    background: transparent;
    text-decoration:none;
    &:active, &:hover {
        outline: 0;
    }
}
pre {
    overflow: auto;
    white-space: pre;
    white-space: pre-wrap;
    word-wrap: break-word;
}
button, select {
    text-transform: none;
}
textarea {
    overflow: auto;
}
::-moz-selection {
    background-color: #FFF7A8;
    color: #444444;
}
::selection {
    background-color: #A6DAFF;
    color: #FFF;
}
```