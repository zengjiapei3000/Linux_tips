# apt-using-man-doc

debian 的包管理工具是 apt, 但是使用中, 不管是 `apt -h`, `apt --help`, `man apt`,都看不到详细的文档, 其实 apt 是把apt的很多功能集成到一起了. 应该去看 `man apt` 对应条目的see also, 比如 `man apt` 下的 `search` 写了一个 `apt-cache(8)`, 就应该去`man apt-cache` 下面看 `search`.