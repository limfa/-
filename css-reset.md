# CSS公共样式重置

```scss
@charset 'UTF-8';
*{
    padding: 0;
    margin: 0;
    border: 0;
    // !todo ie7- not compatible ,like <i> tag has font-style:italic style itself
    font: inherit;
    // !todo ie7- not compatible ,like <a> tag has color style itself
    color: inherit;
}
html{
    color: #000;
    // in chrome ,the min line-height of <input> is 1.4em * 14px;why ? i do't know
    font: normal 14px/1.4em "microsoft yahei", tahoma, arial ;
}
body{
    background-color: #fff;
}
input, button {
    outline: none;
}
input[type=submit], input[type=button], input[type=checkbox], input[type=radio], button {
    cursor: pointer;
}
ul, ol {
    list-style: none;
}
img {
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
    resize: none;
}
// reset selection style
::-moz-selection {
    background-color: #FFF7A8;
    color: #444444;
}
::selection {
    background-color: #A6DAFF;
    color: #FFF;
} 
// remove style webkit itself : "outline: -webkit-focus-ring-color auto 5px;"
:focus {
    outline: none;
}
```