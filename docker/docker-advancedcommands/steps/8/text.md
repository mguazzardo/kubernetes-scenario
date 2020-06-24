
Мы можем завершить наш отдельный контейнер двумя способами.
- Убить его командой **docker kill** (немедленно останавливается).
- Остановка с помощью команды **docker stop** (задержка 10 секунд).

## Stop

Давайте остановим один из контейнеров:

`docker stop mycontainer`{{execute}}

## Kill

Давайте будем менее терпеливы с другими контейнерами:

`docker kill $(docker ps -q)`{{execute}}

> Выше команда будет печатать идентификаторы **IDs** завершенных контейнеров **terminated container(s)**
>
> 13e1e0042b1c
>
> 78e1e0042b1d

Команды **stop** и **kill** могут принимать несколько идентификаторов контейнеров **IDs**.

> **Note:** Давайте проверим, что наши контейнеры больше не отображаются, запустив: `docker ps`{{execute}}