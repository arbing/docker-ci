# docker-ci

docker-ci

## Windows 下修改文件权限

```sh
git ls-tree HEAD
git update-index --chmod=+x mvn-entrypoint.sh
git commit -m "revise permission access"
```
