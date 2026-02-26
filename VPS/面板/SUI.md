[不良林 SUI](https://bulianglin.com/archives/nicename.html)

## 安装S-UI

`VERSION=1.2.2 && bash <(curl -Ls https://raw.githubusercontent.com/alireza0/s-ui/$VERSION/install.sh) $VERSION`


## Reality目标域名

```
for d in acctcdn.msftauth.net s.mp.marsflag.com ts1.tc.mm.bing.net assets.adobedtm.com azure.microsoft.com ocsp2.apple.com www.oracle.com tag.demandbase.com amd.com statici.icloud.com ; do t1=$(date +%s%3N); timeout 1 openssl s_client -connect $d:443 -servername $d </dev/null &>/dev/null && t2=$(date +%s%3N) && echo "$d: $((t2 - t1)) ms" || echo "$d: timeout"; done
```
卸载sui
```
systemctl stop s-ui
systemctl disable s-ui
# 删除二进制执行文件
rm -f /usr/bin/s-ui
# 删除整个配置和数据库目录 (这是最重要的，防止残留数据影响后续安装)
rm -rf /usr/local/s-ui
rm -rf /etc/s-ui/
# 删除系统服务定义文件
rm -f /etc/systemd/system/s-ui.service
rm -f /etc/systemd/system/s-ui.service
rm -f /etc/systemd/system/multi-user.target.wants/s-ui.service
# 刷新系统服务列表
systemctl daemon-reload
```


Global address:
http://69.63.205.187:2095/app/


First admin credentials:
        Username:        EOOPrm8R
        Password:        PQEq5ebA

gsp-ssl.ls.apple.com
ts1.tc.mm.bing.net
ocsp2.apple.com


