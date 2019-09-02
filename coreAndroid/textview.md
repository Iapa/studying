[https://github.com/suragch/AndroidFontMetrics](https://github.com/suragch/AndroidFontMetrics)

![](/assets/textview.png)![](/assets/textview_metrics.png)





```
docker run -d --name=netdata \
```

```
docker run -d --name=netdata \
    -p 19999:19999 \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  netdata/netdata
```



