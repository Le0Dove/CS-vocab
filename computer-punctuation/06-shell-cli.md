# 06. Shell 与命令行 (Shell & CLI)

### Pipe / 管道符
- **中文**：管道符
- **定义**：将前一个命令的输出作为后一个命令输入的符号
- **说明**：ls | grep ".txt"；Unix 哲学核心：小工具组合完成大任务；可多级串联：cmd1 | cmd2 | cmd3；与 >（重定向）不同
- **相关**：>、>>、xargs、Pipeline（管道）

### Output Redirection / 输出重定向
- **中文**：输出重定向
- **定义**：将命令输出写入文件而非终端的符号
- **说明**：echo "hello" > file.txt；覆盖模式（原有内容丢失）；>& 重定向 stderr；文件描述符：1> stdout、2> stderr
- **相关**：>>、<、2>&1、Redirection（重定向）

### Append Redirection / 追加重定向
- **中文**：追加重定向
- **定义**：将命令输出追加到文件末尾而非覆盖的符号
- **说明**：echo "line" >> file.log；保留原有内容；日志记录常用；与 >（覆盖）相对
- **相关**：>、<、Redirection（重定向）

### Input Redirection / 输入重定向
- **中文**：输入重定向
- **定义**：从文件而非键盘获取命令输入的符号
- **说明**：sort < input.txt；Here Document：cat << EOF ... EOF；将文件内容作为命令输入；与 | 不同：| 是进程间，< 是文件到进程
- **相关**：<<、>、Redirection（重定向）

### Here Document / Here Document
- **中文**：Here Document
- **定义**：在脚本中内联多行文本输入的重定向语法
- **说明**：cat << EOF
line1
line2
EOF；定界符（EOF）可自定义；变量会被扩展；<<- 忽略前导制表符
- **相关**：<<<、<、Redirection（重定向）

### Here String / Here String
- **中文**：Here String
- **定义**：将字符串作为输入传递给命令的单行语法
- **说明**：cat <<< "hello"；等价于 echo "hello" | cat；比 Here Document 更简洁；Bash/Zsh 支持
- **相关**：<<、<、Redirection（重定向）

### Background / 后台运行
- **中文**：后台运行
- **定义**：将命令放入后台执行的符号
- **说明**：long_running_task &；立即返回提示符；jobs 查看后台任务；fg 前台化；bg 后台继续；与 nohup 配合防止挂起退出
- **相关**：nohup、fg、bg、jobs、Background Process（后台进程）

### Logical AND / 逻辑与（命令）
- **中文**：逻辑与（命令）
- **定义**：前命令成功时才执行后命令的运算符
- **说明**：mkdir dir && cd dir；前命令返回 0（成功）才执行后命令；与 || 相对：cmd1 || cmd2（前失败才执行后）；短路求值
- **相关**：||、;、Command Chaining（命令链）

### Logical OR / 逻辑或（命令）
- **中文**：逻辑或（命令）
- **定义**：前命令失败时才执行后命令的运算符
- **说明**：cmd1 || echo "cmd1 failed"；前命令返回非 0（失败）才执行后命令；与 && 相对；常用于设置默认值或错误处理
- **相关**：&&、;、Command Chaining（命令链）

### Command Separator / 命令分隔符
- **中文**：命令分隔符
- **定义**：按顺序执行多个命令的分隔符
- **说明**：cmd1 ; cmd2 ; cmd3；无论前命令是否成功都继续执行；与 &&（成功才继续）和 ||（失败才继续）区别；一行写多个命令
- **相关**：&&、||、Command Chaining（命令链）

### Variable / 变量引用
- **中文**：变量引用
- **定义**：Shell 中引用变量值的符号
- **说明**：echo $HOME；${VAR} 更安全的引用方式；$? 上一个命令退出码；$$ 当前进程 ID；$! 最后后台进程 ID；$# 参数个数；$@ 所有参数
- **相关**：Variable（变量）、Parameter Expansion（参数扩展）

### Exit Code / 退出码
- **中文**：退出码
- **定义**：上一个命令的退出状态码
- **说明**：0 表示成功；非 0 表示失败（不同值可表示不同错误）；if [ $? -eq 0 ]; then ... fi；与 &&、|| 配合使用
- **相关**：Exit Status（退出状态）、Error Code（错误码）

### Process ID / 进程 ID
- **中文**：进程 ID
- **定义**：当前 Shell 进程的进程标识符
- **说明**：echo $$；用于创建临时文件：/tmp/tmpfile_$$；唯一标识当前脚本实例；不可修改
- **相关**：$!、PID、Process（进程）

### Background PID / 后台进程 ID
- **中文**：后台进程 ID
- **定义**：最后一个放入后台运行的进程 ID
- **说明**：long_task &；echo $!；可用于等待或 kill 后台进程；wait $! 等待完成
- **相关**：$$、&、Background Process（后台进程）

### All Arguments / 所有参数
- **中文**：所有参数
- **定义**：Shell 脚本中所有位置参数的列表
- **说明**：与 $* 的区别：$@ 保留每个参数的独立性（加引号时 "$@"）；$* 合并为一个字符串；推荐用 "$@" 传递所有参数
- **相关**：$*、$#、$1、Argument（参数）

### Argument Count / 参数个数
- **中文**：参数个数
- **定义**：Shell 脚本中位置参数的数量
- **说明**：if [ $# -ne 2 ]; then echo "Usage: $0 arg1 arg2"; fi；常用于参数校验；不包含 $0（脚本名）
- **相关**：$@、$1、$0、Argument（参数）

### Script Name / 脚本名
- **中文**：脚本名
- **定义**：当前执行的脚本或 Shell 的名称
- **说明**：echo $0；用于显示用法信息：echo "Usage: $0 [options]"；Bash 中 - 表示登录 Shell
- **相关**：$1、$#、$@、Script（脚本）

### Positional Arguments / 位置参数
- **中文**：位置参数
- **定义**：Shell 脚本中按位置传入的参数
- **说明**：$1 第一个参数，$2 第二个...；${10} 起必须加花括号；shift 命令左移参数；用于获取命令行输入
- **相关**：$@、$#、$0、Argument（参数）

### Glob Star / 通配符
- **中文**：通配符
- **定义**：匹配任意字符序列（包括空）的文件名通配符
- **说明**：ls *.txt；匹配所有 .txt 文件；与 ?（匹配单个字符）相对；** 递归匹配子目录（部分 Shell）；正则表达式中含义不同
- **相关**：?、**、Glob、Wildcard（通配符）

### Glob Question / 单字符通配符
- **中文**：单字符通配符
- **定义**：匹配恰好一个任意字符的文件名通配符
- **说明**：ls file?.txt 匹配 file1.txt、fileA.txt；不匹配 file12.txt；与 *（匹配任意长度）相对
- **相关**：*、Glob、Wildcard（通配符）

### Glob Class / 字符类通配
- **中文**：字符类通配
- **定义**：匹配方括号内任一字符的文件名通配符
- **说明**：ls file[0-9].txt；范围：[a-z]、[0-9]；否定：[^abc] 或 [!abc]；与正则表达式字符类类似
- **相关**：*、?、Glob、Character Class（字符类）

### Brace Expansion / 大括号展开
- **中文**：大括号展开
- **定义**：Shell 中生成字符串序列的语法
- **说明**：echo file{1,2,3}.txt → file1.txt file2.txt file3.txt；范围：{1..10}；嵌套：{a,b}{1,2}；与通配不同：展开发生在执行前
- **相关**：()、$()、Glob、Brace Expansion（大括号展开）

### Tilde / 主目录
- **中文**：主目录
- **定义**：表示当前用户主目录的波浪号
- **说明**：cd ~；~user 表示 user 的主目录；echo ~；Shell 自动展开；等价于 $HOME
- **相关**：$HOME、cd、Path（路径）

### Current Directory / 当前目录
- **中文**：当前目录
- **定义**：表示当前工作目录的单点号
- **说明**：./script.sh（执行当前目录脚本）；ls .；与 ..（父目录）相对；PATH 中通常不包含 .（安全考虑）
- **相关**：..、Path（路径）、Directory（目录）

### Parent Directory / 父目录
- **中文**：父目录
- **定义**：表示当前目录的父目录的双点号
- **说明**：cd ..；ls ../file.txt；可连续使用：../../config；与 .（当前目录）相对；文件系统导航基础
- **相关**：.、Path（路径）、Directory（目录）

### Previous Directory / 前一个目录
- **中文**：前一个目录
- **定义**：表示上一次所在目录的短横线
- **说明**：cd -；快速在两个目录间切换；echo $OLDPWD；非常实用的导航快捷方式
- **相关**：cd、~、Directory（目录）

### Root Directory / 根目录
- **中文**：根目录
- **定义**：Unix/Linux 文件系统的顶级目录
- **说明**：cd /；绝对路径以 / 开头：/usr/bin；分隔路径组件：/home/user/file；Windows 用 \ 但 URL 仍用 /
- **相关**：.、..、Path（路径）、Root（根）

### Line Continuation / 续行符
- **中文**：续行符
- **定义**：将长命令折到下一行继续的符号
- **说明**：very_long_command \
--option1 value1 \
--option2 value2；Shell 中反斜杠后紧跟换行；反斜杠前不可有空格
- **相关**：;、Line Continuation（续行）

### Comment / 注释
- **中文**：注释
- **定义**：Shell 脚本中注释行的开始符号
- **说明**：# This is a comment；从 # 到行尾都是注释；Shebang 除外：#!/bin/bash；配置文件中常用
- **相关**：#!、Comment（注释）

### History Expansion / 历史扩展
- **中文**：历史扩展
- **定义**：Bash 中引用历史命令的符号
- **说明**：!! 上一个命令；!n 第 n 个历史命令；!string 最近以 string 开头的命令；!$ 上一个命令的最后一个参数；需启用 history expansion
- **相关**：history、Bash、Command History（命令历史）

### Command Substitution Old / 命令替换（旧）
- **中文**：命令替换（旧）
- **定义**：将命令输出嵌入到另一个命令中的旧语法
- **说明**：echo "Today is `date`"；已过时，现代推荐 $(date)；嵌套困难；反引号内需要转义反引号
- **相关**：$()、Command Substitution（命令替换）

### Command Substitution / 命令替换（新）
- **中文**：命令替换（新）
- **定义**：将命令输出嵌入到另一个命令中的现代语法
- **说明**：echo "Today is $(date)"；可嵌套：$(cmd1 $(cmd2))；现代 Shell 推荐；比反引号 ` ` 更清晰
- **相关**：` `、Command Substitution（命令替换）

### Null Redirection / 丢弃输出
- **中文**：丢弃输出
- **定义**：将输出重定向到空设备文件以丢弃的语法
- **说明**：cmd > /dev/null 2>&1；标准输出和标准错误都丢弃；/dev/null 是特殊文件，写入即丢弃；Linux/Unix 通用
- **相关**：>、2>&1、/dev/null、Redirection（重定向）

### Stderr to Stdout / 错误重定向到输出
- **中文**：错误重定向到输出
- **定义**：将标准错误（stderr）重定向到标准输出（stdout）的语法
- **说明**：cmd > file.log 2>&1；合并输出和错误到同一文件；顺序很重要：2>&1 必须在文件重定向之后；等价于 >&（Bash）
- **相关**：>、>&、stderr、stdout、Redirection（重定向）

### Nohup / 不挂断
- **中文**：不挂断
- **定义**：使命令在用户退出后仍继续运行的工具
- **说明**：nohup long_task &；输出默认重定向到 nohup.out；忽略 SIGHUP 信号；后台任务长期运行必备
- **相关**：&、disown、SIGHUP、Background Process（后台进程）

### Xargs / 参数传递
- **中文**：参数传递
- **定义**：从标准输入构建并执行命令的工具
- **说明**：find . -name "*.txt" | xargs rm；处理大量文件（避免 Argument list too long）；-I {} 占位符：ls | xargs -I {} cp {} backup/；-n 限制每批参数数
- **相关**：|、find、exec、Pipeline（管道）

### Env / 环境变量
- **中文**：环境变量
- **定义**：查看或设置环境变量的命令
- **说明**：env 查看所有；env VAR=value cmd 临时设置并运行；printenv VAR 查看特定变量；export VAR=value 导出到子进程
- **相关**：export、$VAR、Environment Variable（环境变量）

### Export / 导出变量
- **中文**：导出变量
- **定义**：将 Shell 变量导出为环境变量供子进程使用的命令
- **说明**：export PATH=$PATH:/new/path；export MY_VAR="value"；仅对当前 Shell 及子进程有效；写入 ~/.bashrc 持久化
- **相关**：env、source、Variable（变量）

### Source /  sourcing
- **中文**： sourcing
- **定义**：在当前 Shell 环境中执行脚本文件的命令
- **说明**：source ~/.bashrc 或 . ~/.bashrc；与 ./script.sh 不同：后者在子 Shell 执行，source 在当前 Shell；用于加载配置
- **相关**：.、export、Shell Script（Shell 脚本）

### Alias / 别名
- **中文**：别名
- **定义**：为命令创建短名称的命令
- **说明**：alias ll='ls -alF'；临时生效；写入 ~/.bashrc 持久化；unalias ll 取消；type ll 查看定义
- **相关**：function、Shell、Shortcut（快捷方式）

### Chmod / 改权限
- **中文**：改权限
- **定义**：修改文件或目录权限的命令
- **说明**：chmod 755 file；数字模式：r=4, w=2, x=1；符号模式：chmod u+x file；递归：chmod -R 755 dir；常用：644（文件）、755（目录）
- **相关**：chown、ls -l、Permission（权限）

### Chown / 改所有者
- **中文**：改所有者
- **定义**：修改文件或目录所有者和组的命令
- **说明**：chown user:group file；仅 root 或文件所有者可用（部分情况）；递归：chown -R user:group dir；与 chmod 配合管理权限
- **相关**：chmod、Permission（权限）、Ownership（所有权）

### Grep / 全局正则打印
- **中文**：全局正则打印
- **全称**：Global Regular Expression Print
- **定义**：按模式搜索文本的强大工具
- **说明**：grep "pattern" file；选项：-i（忽略大小写）、-v（反向匹配）、-r（递归）、-n（显示行号）、-E（扩展正则）；egrep、fgrep 变体
- **相关**：regex、awk、sed、Search（搜索）

### Sed / 流编辑器
- **中文**：流编辑器
- **全称**：Stream Editor
- **定义**：对文本进行过滤和转换的流处理工具
- **说明**：sed 's/old/new/g' file；s/// 替换；d 删除；p 打印；-i 就地编辑；支持正则表达式；处理大文件效率高
- **相关**：awk、grep、regex、Text Processing（文本处理）

### Awk / 文本处理
- **中文**：文本处理
- **定义**：按列处理文本数据的编程语言/工具
- **说明**：awk '{print $1}' file；$0 整行，$1 第一列；条件过滤：awk '$3 > 100 {print}'；BEGIN/END 块；功能强大，可视为迷你语言
- **相关**：sed、grep、Text Processing（文本处理）

### Tar / 归档
- **中文**：归档
- **定义**：将多个文件打包为单个归档文件的工具
- **说明**：tar -czvf archive.tar.gz dir/；c 创建、x 解压、t 列表、z gzip、j bzip2、J xz、v 详细、f 文件；常用组合：tar -xzf file.tar.gz
- **相关**：gzip、zip、Archive（归档）

### Curl / 传输工具
- **中文**：传输工具
- **定义**：命令行下传输数据的工具，支持多种协议
- **说明**：curl https://api.example.com；选项：-X POST、-H "Header"、-d "data"、-o file、-L 跟随重定向、-v 详细；HTTP/FTP/SFTP 等协议
- **相关**：wget、HTTP、API、Network（网络）
