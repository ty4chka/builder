# gh-builder — личная сборочная на GitHub Actions

Любые компиляции в облаке, бинарники приходят в Release.

## Как пользоваться (из Termux)

### Запуск сборки
gh workflow run build.yml \
  -f repo_url=Godde3s/omnirouter \
  -f build_cmd="CGO_ENABLED=0 go build -trimpath -ldflags=\"-s -w\" -o omnirouter ." \
  -f artifact_glob="omnirouter" \
  -f release_tag=v1.4.0-arm64

### Смотреть статус
gh run list --limit 5
gh run watch

### Скачать бинарники
gh release download <tag> -p "*" -D ./out

### Не только компиляция

В workflow можно любой build_cmd: тесты, линтер, распаковка,
скрипты python/node — что угодно, что выполняется в шелле.

