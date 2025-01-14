### Добро пожаловать

Для мониторинга приложения, работающего в Kubernetes (k8s), вам нужны logs и метрики из приложения, в среда k8s, в которой оно выполняется. 
Использование Elasticsearch, Kibana и Beats позволяет собирать, искать, анализировать и визуализировать все эти данные о приложении и k8s (pods, containers, etc) в одном месте.

### Давайте посмотрим на цель

Это одна из готовых панелей мониторинга dashboards, которые вы увидите, когда развернете примеры приложений и Beats (облегченные средства доставки Elastic для logs, metrics, etc.) в среде Katacoda подключите Beats к службе Elasticsearch в Elastic Cloud. Эта панель метрик Docker, которая поставляется вместе с Metricbeat. Это позволяет анализировать использование CPU и Memory для каждого контейнера, позволяет детализировать данные до определенного контейнера и containers per node. Смотреть на панель инструментов гораздо проще, чем запускать эквивалентные команды kubectl logs, events, top, describe, etc. commands

![Docker Dash](https://user-images.githubusercontent.com/25182304/44353691-c2bb8c00-a475-11e8-8d0e-9578c5c8cc47.png)

### Это пример аннотаций для указания, какой модуль Beat использовать: 
![apache2 module hint](https://user-images.githubusercontent.com/25182304/44863869-50546400-ac4c-11e8-892d-5575af08a724.png)

### Это hint для указания правила многострочного парсинга для неизвестного log type: 
![Spring multiline hint](https://user-images.githubusercontent.com/25182304/44864163-f86a2d00-ac4c-11e8-874c-ae01eae43864.png)

###  Перед тем как продолжить
Этот сценарий зависит от наличия Elasticsearch и Kibana. Инструкции вызывают экземпляр службы Elasticsearch Service в Elastic Cloud. Разверните Elasticsearch Service перед запуском сценария.


### Create an Elastic Cloud deployment
Вы можете использовать Elasticsearch Service в Elastic Cloud ( http://cloud.elastic.co ), либо локальное развертывание, либо развернуть контейнеры с https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

Если это ваш первый опыт использования стека Elastic, я бы порекомендовал Elastic Cloud; и не волнуйтесь, вам не нужна кредитная карта.

Обязательно обратите внимание на идентификатор CLOUD ID и Elastic Password, если вы используете Elastic Cloud или Elastic Cloud Enterprise.

### Быстрый учебник по Katacoda 

Если вы впервые используете Katacoda, позвольте мне представить несколько интересных идей:

* В общем, вам не нужно печатать команды в терменале. В большинстве случаев вы можете просто (Кликнуть - click) команду в инструкции для ее запуска. 
* Если вам нужен доступ к веб-браузеру, поищите вкладки в верхней части окна терминала. В этом курсе вам понадобятся две страницы - одна для приложени Guestbook, а другая для Kibana. Вы должны увидеть вкладку *Guestbook* tab и вкладку *Kibana* tab в терминале.  Запустив приложение Guestbook, (Кликнуть - click) на вкладку *Guestbook* tab  чтобы открыть его в окне браузера и ввести несколько записей. Аналогично, после запуска Kibana вы должны открыть эту вкладку и посмотреть на данные.
* Каждый раз, когда вы запускаете или перезапускаете курс, все сбрасывается. Если вы что-то неправильно настроили, просто перезапустите курс.




