Введение в **Pods**.

В этой лабораторной работе мы рассмотрим, как запускать контейнеры в **Pods**.

**Pods** являются основными строительными блоками **Kubernetes**.
**Pods** - это **группы контейнеров с общими пространствами имен и общими томами - shared volumes**.

* **Pods** для контейнеров всегда расположены на одном **host**
* **Pod containers** совместно используют один **IP** и **portspace** и взаимодействуют через localhost
* **Pod containers** имеют доступ к общим томам для хранения **shared volumes**
* **Pods** разработаны, чтобы быть **ephemeral (like cattle, not pets)**

В этой лабораторной работе мы рассмотрим следующее:

## Создание Pods с помощью командной строки

Использование командной строки - это простой способ изучить концепции **pod concepts**.
Эти лабораторные занятия позволят вам изучить **pod configurations**, запустить контейнеры и сети.

## Создание Pods с файлами манифеста - manifest files

Для **production systems** использование командной строки может быть подвержено ошибкам.
В этом упражнении мы рассмотрим **specification** и создание **Pods** на основе файла.

## Инспекция Pods

Понимание того, как работает **pod**, поможет вам отладить проблемы, когда они появятся.
В этой лабораторной работе мы рассмотрим жизненный цикл пода **Pod lifecycl**e, сетевое взаимодействие и конфигурацию.

Для получения дополнительной информации см. Kubernetes [documentation][docs].

<!-- Links Referenced -->

[docs]:           https://kubernetes.io/docs/concepts/workloads/pods/pod/
