# 2.1 调用一个脚本

写完一个脚本以后，你可以通过`sh scriptname`[^1]或`bash scriptname`来调用它（不推荐使用`sh <scriptname`调用脚本，因为这会禁用脚本从标准输入（stdin）读入数据）。更方便的方式是使用`chmod`命令使脚本可以被直接执行。

执行命令：

`chmod 555 scriptname`（给予所有用户读取/执行的权限）[^2]

或

`chmod +rx scriptname`（给予所有用户读取/执行的权限）

`chmod u+rx scriptname`（仅给予脚本所有者读取/执行的权限）

当脚本的权限被设置好后，你就可以直接使用`./scriptname`[^3]进行调用测试了。如果脚本文件以sha-bang开头，那么它将自动调用指定的命令解释器运行脚本。

完成调试与测试后，你可能会将脚本文件移至`/usr/local/bin`（使用root权限）中，使脚本可以被所有用户调用。这时你可以直接在命令行中输入`scriptname [ENTER]`执行脚本。

## 注记

{% hint style="info" %}
[1] 注意，当你使用`sh scriptname`调用*Bash*脚本时，将会禁用与Bash特性相关的功能，脚本有可能会执行失败。

[2] 脚本需要同时具有读取和执行的权限，因为shell需要读取脚本执行。

[3] 为什么不直接使用`scriptname`来调用脚本？为什么当工作目录（$PWD）正好是`scriptname`所在目录时也不起作用？因为一些安全原因，当前目录（`./`）并不会被默认添加到用户的$PATH路径中。因此需要用户显式使用`./scriptname`在当前目录下调用脚本。
{% endhint %}

[^1]: 注意，当你使用`sh scriptname`调用*Bash*脚本时，将会禁用与Bash特性相关的功能，脚本有可能会执行失败。
[^2]: 脚本需要同时具有读取和执行的权限，因为shell需要读取脚本执行。
[^3]: 为什么不直接使用`scriptname`来调用脚本？为什么当工作目录（$PWD）正好是`scriptname`所在目录时也不起作用？因为一些安全原因，当前目录（`./`）并不会被默认添加到用户的$PATH路径中。因此需要用户显式使用`./scriptname`在当前目录下调用脚本。
