# 中文 Manpages 手册翻译

## 第一步：预翻译

本 repo 用来管理英文手册并对翻译前的英文文档进行错误修复和格式处理，以便更好地被翻译者利用，本 repo 地址在 <https://github.com/manpages-zh/Pretranslation>.

如果您希望我们来翻译一篇手册，您应在此添加该文件。您也可以自己来翻译，为了您的翻译更好的被利用，请您移步至 <https://github.com/manpages-zh/Translate>.

-----------------------------------------------------------------

预翻译是翻译的准备阶段，这里我们使用纯文本的超文本标记语言 HTML 作为翻译格式，HTML 可以在任何浏览器打开，它通用易扩展的特性使我们可以容易的将其转换为排版所需的格式。

您自己也可以很容易将 man 手册转换为 html 文件，man 的` -H `选项将任意的手册转换为网页文件，并在您电脑中默认浏览器（如果没有没有指定，则通常选择 lynx）中打开。下面是该选项的介绍。

-H[browser], --html[=browser]

This  option  will  cause groff to produce HTML output, and will display that output in a web browser.  The choice of browser  is determined  by the optional browser argument if one is provided, by the $BROWSER  environment  variable,  or  by  a  compile-time default  if  that  is unset (usually lynx).  This option implies -t, and will only work with GNU troff.

----------------------------------------------

打开后您可以检查这个文件，并保存。可以发现，对于大多数手册，生成的 html 文件都没有错误，但如果手册包含表格（比如 bash 手册)，那么 man 会默认使用图片来保存，但这个图片大概因为丢失而不能被访问，所以网页会显示一个方框，这应该是 man 的 bug,如果遇到这个问题，我们建议您使用 man2html 来生成 html 文档。大多数 Linux 发行版都包含 man2html 这个小程序，您可以使用包管理器来安装这个程序，使用它也非常简单，通常我们用到下面两个命令。

`man2html [-options]  < infile   > outfile`

`man bash... | man2html [-options]  > outfile`

第一个命令中 infile 为输入文件，outfile 为输出文件，需要注意的是，infile 的地址是绝对地址，而且只能作用于 nroff 格式，通常您电脑中的手册都是压缩的，man 在调用这些手册的时候自动解压，但您在使用这个命令的时候应手动解压缩。如果您觉得不便，希望像平时使用 man 那样生成 html 文件，那么第二个命令非常适合您。

第二个命令的前半部分就是您通常使用的 man 命令，通过 `|` 管道发送给 man2html. 后半部分就是 man2html 的命令了。通常直接使用该命令会出现换行错误，和 `man -H` 不同，man2html 生成的文件每行80列，多出来的就换到下一行，如果一个单词在换行处没有连词号，就会出现这个问题，解决方法是使用下面的命令，这里以 bash 文档作为例子。

`man --nh bash | man2html >man.html`

您可以发现这里多加了一个 `--nh` 选项，这个选项的解释如下：

--no-hyphenation, --nh

              Normally, nroff will automatically hyphenate text at line breaks
              even in words that do not contain hyphens, if it is necessary to
              do so to lay out words on  a  line  without  excessive  spacing.
              This  option  disables automatic hyphenation, so words will only
              be hyphenated if they already contain hyphens.

              If you are writing a manual page  and  simply  want  to  prevent
              nroff  from hyphenating a word at an inappropriate point, do not
              use this option, but consult the  nroff  documentation  instead;
              for instance, you can put "\%" inside a word to indicate that it
              may be hyphenated at that point, or put "\%" at the start  of  a
              word to prevent it from being hyphenated.

------------------------------------------------------------

# 加入我们


翻译是简单的，您的翻译成果也会和他人分享。我们欢迎任何希望改善中文手册的伙伴们加入。

我们需要你的帮助来改善中文手册。
