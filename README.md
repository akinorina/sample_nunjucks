# Nunjucks テンプレートエンジンを Express で使うサンプル

## 手順

<dl>
<dt>1. Express-Generator でスケルトンコードを生成</dt>
<dd>

```bash
% express --view=twig sample_nunjucks  (実際は親ディレクトリで実行している)
% npm install
% npm run start
```

Web ブラウザで http://localhost:3000 へアクセス、一応、ここまで動作することを確認。

</dd>

<dt>2. Nunjucks テンプレートエンジンをインストール</dt>
<dd>
% npm install nunjucks
</dd>

<dt>3. twig テンプレートエンジンをアンインストール</dt>
<dd>
% npm uninstall twing
</dd>

<dt>4. nunjucks テンプレート用にコードを変更</dt>
<dd>

app.js を編集

```javascript
var logger = require('morgan');
var nunjucks = require('nunjucks');                    // <-- 追加
var indexRouter = require('./routes/index');
var usersRouter = require('./routes/users');

var app = express();

// view engine setup
nunjucks.configure('views', {                          // <-- ここから４行追加
  autoescape: true,
  express: app
});

app.set('views', path.join(\_\_dirname, 'views'));     //
app.set('view engine', 'html');                        // <-- この第２パラメータ 'html' がテンプレートファイルの拡張子になる。
```

views/layout.twig を views/layout.html に rename する。  
views/index.twig を views/index.html に rename する。  
views/index.html の layout 指定を layout.html に変更 する。  
views/error.twig を views/error.html に rename する。  
views/error.html の layout 指定を layout.html に変更 する。

</dd>

<dt>5. 実行</dt>
<dd>

% npm run start

</dd>
