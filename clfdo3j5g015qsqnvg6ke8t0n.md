---
title: "Find which process listens to a port"
datePublished: Tue Mar 14 2023 10:45:00 GMT+0000 (Coordinated Universal Time)
cuid: clfdo3j5g015qsqnvg6ke8t0n
slug: find-which-process-listens-to-a-port
canonical: https://emresahin.net/find-which-process-listens-to-a-port/

---

Sometimes I need to find out which process listens to a port to kill it.

On macOS,

    sudo lsof -i -P | grep LISTEN | grep :$PORT
    

and on Linux

    netstat -pntl | grep $PORT