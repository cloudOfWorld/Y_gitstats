# Y_gitstats

使用gitstats，进行git代码统计

OS X install gitstats
1 安装gitstat：

1) brew install --HEAD homebrew/head-only/gitstats  

有更详细安装方法 http://gitstats.sourceforge.net/

2) brew install gnuplot

To minimise my effort, I tend to use package managers to install command line tools as much as possible.
For OS X I recommend using homebrew. Installing gnuplot with homebrew is as easy as typing: brew install gnuplot

2. 使用：

  1)下载代码到code目录  
  git clone ssh://xxxx@xxxx29418/xxxxx code  

  2)使用gitstat工具分析code目录代码生成结果到result中
  gitstats code result  

3. result下生产html分析报告
    分析结果：
    常规的统计：文件总数，行数，提交量，作者数。
    活跃性：每天中每小时的、每周中每天的、每周中每小时的、每年中每月的、每年的提交量。
    作者数：列举所有的作者（提交数，第一次提交日期，最近一次的提交日期），并按月和年来划分。
    文件数：按日期划分，按扩展名名划分。
    行数：按日期划分。
    Linux代码的分析例子：   http://gitstats.sourceforge.net/examples/linux-2.6/index.html

命令行
查看git上的个人代码量：
git log --author="username" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -
结果示例：(记得修改 username)

added lines: 120745, removed lines: 71738, total lines: 49007
统计每个人增删行数
git log --format='%aN' | sort -u | while read name; do echo -en "$name\t"; git log --author="$name" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -; done
结果示例

Max-laptop    added lines: 1192, removed lines: 748, total lines: 444
chengshuai    added lines: 120745, removed lines: 71738, total lines: 49007
cisen    added lines: 3248, removed lines: 1719, total lines: 1529
max-h    added lines: 1002, removed lines: 473, total lines: 529
max-l    added lines: 2440, removed lines: 617, total lines: 1823
mw    added lines: 148721, removed lines: 6709, total lines: 142012
spider    added lines: 2799, removed lines: 1053, total lines: 1746
thy    added lines: 34616, removed lines: 13368, total lines: 21248
wmao    added lines: 12, removed lines: 8, total lines: 4
xrl    added lines: 10292, removed lines: 6024, total lines: 4268
yunfei.huang    added lines: 427, removed lines: 10, total lines: 417
³ö    added lines: 5, removed lines: 3, total lines: 2
查看仓库提交者排名前 5
git log --pretty='%aN' | sort | uniq -c | sort -k1 -n -r | head -n 5
贡献值统计
git log --pretty='%aN' | sort -u | wc -l
提交数统计
git log --oneline | wc -l
添加或修改的代码行数：
git log --stat|perl -ne 'END { print $c } $c += $1 if /(\d+) insertions/'

参考：https://segmentfault.com/a/1190000008542123
