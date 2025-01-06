# jp-univ-math-exams
## はじめに
東京大学、京都大学の過去50年分の数学の入試問題は、例えば以下の本で解答付きで入手できます。
- [東大・入試数学50年の軌跡【1971年～2020年】](https://ts-webstore.net/?pid=155897720)
- [京大・入試数学51年の軌跡【1971年～2021年】](https://ts-webstore.net/?pid=163820149)

このリポジトリは、これらの本で扱っていない入試問題の解答を作成を目的にしています。
すなわち、2021年以降の東京大学と、2022年以降の京都大学の入試問題の解答を作成し、蓄積していこうと思います。

## フォルダ構成
PDFファイルとLaTeXのコード(tex)ファイルの両方を共有します。受験生はLaTeXについて知らなくても問題ないですが、いずれ数学の論文を記載する際に必須となります。問題だけのファイルは、"problem_xxx"、問題および解答が一緒のファイルは、"solution_xxx"と命名します。"xxx"部分で、前期、後期や理系、文系などの分類をします。pictureフォルダは、LaTeXのコードで使用する図を配置します。図は基本的に[GeoGebra](https://www.geogebra.org/?lang=ja)で作成します。
<pre>
university-name/
├── 2022/
│   ├── picture/
│   │   └── picture1.png
│   ├── problem_xxx.pdf
│   └── problem_xxx.tex
│   └── solution_xxx.pdf
│   └── solution_xxx.tex
</pre>

## LaTeXの環境構築について
以下のサイトを参考にしました。
- [VSCode と WSL2 で LaTeX 執筆環境を作ろう](https://zenn.dev/minatoneko/articles/b4038eb6524199)
- [VSCode で最高の LaTeX 環境を作る](https://qiita.com/rainbartown/items/d7718f12d71e688f3573)
- [VSCodeでのLaTeXの環境構築](https://zenn.dev/hash_yuki/articles/31855fbdb5fdf7)

うろ覚えですが、次の手順で環境構築できるはずです。(詳細は上記サイトを確認してください)
1. TeXLiveのインストール
2. Visual Studio Codeのインストール
3. Visual Studio Codeの拡張機能"LaTeX Workshop"のインストール (made by James Yu)
4. Visual Studio Codeの設定ファイル"settings.json"を開き、"latex-workshop.latex.tools"の設定を追加(既にsettings.jsonに"latex-workshop.latex.tools"がある場合は、四角括弧[]の中身を追加)
    ```
    "latex-workshop.latex.tools": [
            {
                "name": "platex",
                "command": "platex",
                "args": [
                    "-interaction=nonstopmode",
                    "%DOC%"
                ]
            },
            {
                "name": "dvipdfmx",
                "command": "dvipdfmx",
                "args":[
                    "-V 4",
                    "%DOC%"
                ]
            },
    ]
    ```
5. 同様にsettings.jsonに"latex-workshop.latex.recipes"の設定を追加
    ```
    "latex-workshop.latex.recipes": [
        {
            "name": "platex × 2 → dvipdfmx",
            "tools": [
                "platex",
                "platex",
                "dvipdfmx"
            ]
        },
    ]
    ```

無事に環境構築ができれば、Visual Studio Codeでtexファイルを編集する際に次のコマンドが働くはずです。
- Ctrl + Alt + b : texファイルをpdfファイルに変換
- Ctrl + Alt + v : pdfファイルの表示

## 指摘、質問、要望などについて
[Issue](https://github.com/tt0801/jp-univ-math-exams/issues)にて、お願いします。全て対応できるか分かりませんが、時間の許す限り対応いたします。また、数学の問題に関係する事柄のみならず、LaTeXのコードについて改善点や、より良い図の作成方法などアドバイスがありましたら、遠慮なくIssueで教えてくださると助かります。
