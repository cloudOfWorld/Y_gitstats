# Y_gitstats
OS X install gitstats
1 安装gitstat：
1. brew install --HEAD homebrew/head-only/gitstats  有更详细安装方法 http://gitstats.sourceforge.net/
2. Install gnuplot 5.0.1 on OSX
To minimise my effort, I tend to use package managers to install command line tools as much as possible.
For OS X I recommend using homebrew. Installing gnuplot with homebrew is as easy as typing: brew install gnuplot

2 使用：
  下载代码到code目录  
1. git clone ssh://xxxx@xxxx29418/xxxxx code  

  使用gitstat工具分析code目录代码生成结果到result中
1. gitstats code result  

  result下生产html分析报告 3 分析结果：   常规的统计：文件总数，行数，提交量，作者数。   活跃性：每天中每小时的、每周中每天的、每周中每小时的、每年中每月的、每年的提交量。   作者数：列举所有的作者（提交数，第一次提交日期，最近一次的提交日期），并按月和年来划分。   文件数：按日期划分，按扩展名名划分。   行数：按日期划分。 4 Linux代码的分析例子：   http://gitstats.sourceforge.net/examples/linux-2.6/index.html
