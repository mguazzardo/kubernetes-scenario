## Kubeflow CLI

Также доступен стандартный инструмент командной строки для **Kubeflow**, **`kfctl`**.

`kfctl version`{{execute}}

Всякий раз, когда вы добавляете инструмент **CLI tool**, часто появляется функция завершения, которая позволяет полезно заполнить контекст для параметров командной строки с помощью клавиши табуляции.

`source <(kfctl completion bash)`{{execute}}

## Kubeflow Dashboard

Перейдите на [Kubeflow dashboard](https://[[HOST_SUBDOMAIN]]-31380-[[KATACODA_HOST]].environments.katacoda.com/) и начните изучать его возможности. Доступ к информационной панели также можно получить из вкладки над командной строкой.

При первом появлении на панели управления **Dashboard** будет предложено создать первое рабочее пространство, называемое пространством имен **Namespace**. Используйте предложенное имя **`anonymous`**. Это пространство имен, которое вы называете, будет совпадать с созданным пространством имен **Kubernetes**.

`kubectl get namespaces`{{execute}}

Вы также увидите, что пространство имен было аннотировано и помечено **annotated and labeled**, чтобы оно было распознано **Kubeflow** и **Istio**.

`kubectl describe namespaces anonymous`{{execute}}