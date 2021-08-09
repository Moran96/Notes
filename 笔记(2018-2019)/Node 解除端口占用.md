- 常规情况
`ctrl + c`

- 若不小心 `ctrl + z` 退出进程，或 `node ~/example.js &` 操作
`netstat -tpln` 或 `netstat -nap | grep node` 查看进程ID(即ProcessID)
`kill -9 [PID]` 强制销毁
