```css
/**
 *  @file       reset.css
 *  @brief      reset css styles
 *
 *
 *  @author     liumoran@outlook.com
 *  @version    1.1
 *  @date       2019
*/

/* layout */
* {
    margin: 0;
    padding: 0;
}

html, body{
    height: 100%;
}


/* style */
a {
    text-decoration: none;
    color: black;
}

p {
    font-family: Arial, "Microsoft YaHei", "Microsoft YaHei UI", "微软雅黑", Helvetica, Tahoma, STXihei, "华文细黑", SimSun, "宋体", Heiti, "黑体", sans-serif;
}

em {
    font-style: normal;
}

li {
    list-style: none;
}

input, button ,textarea {
    border: 0;
    outline: none;
    background-color: rgba(0, 0, 0, 0);
}

textarea {
    resize: none;
}

/* float */
.fl{
    float: left;
}
.fr{
    float: right;
}
.clear{
    clear: both;
}
.clearfix:after{
    content: "";
    display: block;
    clear: both;
}

/*      init    placeholder      */
input::-webkit-input-placeholder {
    color: #d3def6;
    font-size: 20px;
    text-align: left;
}
```