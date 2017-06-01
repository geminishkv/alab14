## Laboratory work XIV

Данная лабораторная работа посвещена изучению инструментов для подписывания и верификации исполняемых файлов на примере **codesign**

```bash
$ open http://bd808.com/blog/2013/10/21/creating-a-self-signed-code-certificate-for-xcode/
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab14** на сервисе **GitHub**
- [ ] 2. Ознакомиться со ссылками учебного материала
- [ ] 3. Сгенерировать самоподписанный сертификат
- [ ] 4. Выполнить инструкцию учебного материала
- [ ] 5. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```bash
$ export GITHUB_USERNAME=<имя_пользователя>
```

```bash
$ git clone https://github.com/${GITHUB_USERNAME}/lab13 lab14
$ cd lab14
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab14
```

```bash
$ cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
$ cmake --build _build
$ cmake --build _build --target install
```

```bash
$ codesign -s "Your Company, Inc." ./_install/bin/demo
$ codesign -v ./_install/bin/demo
```

```bash
$ travis setup releases
$ cat .travis.yml
```

```bash
$ cat >> .travis.yml <<EOF
before_deploy:
- codesign -s "Your Company, Inc." ./_install/bin/demo
EOF
```

```bash
$ git add .
$ git commit -m"added code signing"
$ git push origin master
```

```bash
$ travis login --auto
$ travis enable
```

```bash
$ git tag v0.1.0
$ git push origin master
```

## Report

```bash
$ cd ~/workspace/labs/
$ export LAB_NUMBER=14
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m"lab${LAB_NUMBER}"
```

## Links

- [Code Sign macOS](https://www.digicert.com/code-signing/mac-os-codesign-tool.htm)
- [Code Sign Windows](https://msdn.microsoft.com/ru-ru/library/windows/desktop/aa380259(v=vs.85).aspx)
- [Code Sign Unix](https://github.com/bartman/elfgpg)

```
Copyright (c) 2017 Братья Вершинины
```
