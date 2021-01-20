# OA's Node scss 轉換工具

OA's Node scss 轉換工具 📝


## 說明
基於 npm 上的 [sass](https://www.npmjs.com/package/sass) 開發的應用工具，同時加入些許 [compass](http://compass-style.org/) 相關的 [`mixin`](https://sass-lang.com/documentation/at-rules/mixin) 或 [`function`](https://sass-lang.com/documentation/at-rules/function) 以便於使用。

## 安裝

```shell
npm install @oawu/scss
```


## 使用

引入 `require('@oawu/scss')` 即可使用 **scss** 功能，如下範例：

```javascript

  const SCSS = require('@oawu/scss')

  SCSS.file('/paths.../some.scss', result => {
    // done..
  }, error => {
    // fail..
  })

  // or
  SCSS.data('$w: 100px; div { width: $w; }', result => {
    // done..
  }, error => {
    // fail..
  })

```

## 其他功能

可以使用 `@import "@";` 來使用此套件的相關功能，其參考目錄為 [Libs](https://github.com/comdan66/node-Scss/tree/master/Libs)

```scss
  @import "@";

  * {
    &, &:after, &:before {
      vertical-align: top;
      @include box-sizing(border-box);
      @include font-smoothing(subpixel-antialiased);
    }
  }
```

若要使用 Libs 下的其他功能，例如 `CSS3/Cursor` 內所有功能與 `CSS3/Font/Face.scss`，使用方式如下：

```scss

  @import "@/CSS3/Cursor";
  @import "@/CSS3/Font/Face";

```


### 特殊功能

可以使用 `@import "Lalilo";` 來快速使用 [Lalilo](https://github.com/comdan66/Lalilo) 框架常用功能，其引入的功能可以參考 [`Lalilo.scss`](https://github.com/comdan66/node-Scss/blob/master/Libs/Lalilo.scss) 此檔案。

```scss
  @import "Lalilo";

  * {
    &, &:after, &:before {
      vertical-align: top;
      @include box-sizing(border-box);
      @include font-smoothing(subpixel-antialiased);
    }
  }
```

由於 `@import "Lalilo";` 為直接指定的快取檔案，主要目的是為了加快編譯速度，當然您可以自定義引入的檔案內容。

預設的快取檔案為 [`Lalilo.scss`](https://github.com/comdan66/node-Scss/blob/master/Libs/Lalilo.scss)，但可以使用 `Scss.contents` 來改變快取檔案內容。

以下範例為改變 `@import "Lalilo";` 後所引入的內容：

```javascript

  const SCSS = require('@oawu/scss')
  SCSS.contents = "%-tmp {}"

```

```scss
  @import "Lalilo";

  div {
    @extend %-tmp;
  }
```

## 參考 
* compass 功能參考:
  * [https://github.com/Igosuki/compass-mixins](https://github.com/Igosuki/compass-mixins)
  * [https://www.npmjs.com/package/compass-mixins](https://www.npmjs.com/package/compass-mixins)
