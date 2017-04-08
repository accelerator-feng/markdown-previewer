<template>
    <div id='app'>
        <textarea v-model='message' class='text'></textarea>
        <p v-html='previewedMessage' class='view'></p>
    </div>
</template>
<script>
import marked from '../node_modules/marked/marked.min.js'
let message =
    `Heading
=======

Sub-heading
-----------
 
### Another deeper heading
 
Paragraphs are separated
by a blank line.

Leave 2 spaces at the end of a line to do a  
line break

Text attributes *italic*, **bold**, 
\`monospace\`, ~~strikethrough~~ .

Shopping list:

  * apples
  * oranges
  * pears

Numbered list:

  1. apples
  2. oranges
  3. pears

The rain---not the reign---in
Spain.

 *[Herman Fassett](http:freecodecamp.com/hermanfassett)*`;
marked.setOptions({
    renderer: new marked.Renderer(),
    gfm: true,
    tables: true,
    breaks: false,
    pedantic: false,
    sanitize: true,
    smartLists: true,
    smartypants: false
});
export default {
    data() {
            return {
                message
            }
        },
        computed: {
            previewedMessage: function() {
                return marked(this.message);
            }
        }
}
</script>
<style>
#app {
    width: 80%;
    margin: 40px auto;
    font-family: Helvetica, Arial, sans-serif;
}

.view {
    float: right;
    width: 50%;
    margin: 0;
    font-family: Helvetica, Arial, sans-serif;
    font-size: 14px;
    line-height: 1.42857143;
    color: #333;
}

a {
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}

.text {
    display: inline-block;
    max-width: 45%;
    min-width: 45%;
    height: 500px;
    overflow: scroll;
    font-family: Helvetica, Arial, sans-serif;
    padding: 6px 12px;
    font-size: 14px;
    line-height: 1.42857143;
    color: #555;
}
</style>
