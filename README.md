# katexWithDelimiters
Allow rendering of mixed String that contains Math Expressions and other text
in katex RenderToString
# Support
 - \\( Math  \\)

 - $$ Math  $$
# Install
add this function to your project
```js
function renderWithDelimitersToString(text)
{
   var CleanAndRender=function(str){return katex.renderToString(str.replace(/\\\(|\$\$|\\\)/g,""));}	
   return text.replace(/(\\\([^]*?\\\))|(\$\$[^]*?\$\$)/g, function(m, bracket, dollar) {
        if (bracket !== undefined) return CleanAndRender(m);
        if (dollar !== undefined) 
        return "<p style='width:100%;text-align:center;'>" + CleanAndRender(m) + "</p>";
        return m;
   });
}	
```
# Usage
=
```js
var result= renderWithDelimitersToString("this is an equation $$ y=x^{-2} $$ ");
```
