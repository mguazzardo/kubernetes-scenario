Термин **service mesh** используется для описания сети микросервисов **network of microservices**, которые составляют такие приложения, и взаимодействия между ними. По мере того, как размер и сложность **service mesh** увеличиваются, ее становится все труднее понять и контролировать. Его требования могут включать **discovery**, балансировку нагрузки, восстановление после сбоев, метрики и мониторинг. **Service mesh** также часто имеет более сложные эксплуатационные требования, такие как A/B testing, аварийные выпуски, ограничение скорости, контроль доступа и сквозная аутентификация.

**Istio** обеспечивает понимание поведения и оперативный контроль всей **service mesh** в целом, предлагая комплексное решение для удовлетворения разнообразных требований приложений микросервиса. Он предоставляет ряд ключевых возможностей в сети сервисов **network of services**:

- **Traffic Management**. Контролируйте поток трафика **flow of traffic** и **API calls** между сервисами, повышайте надежность вызовов и повышайте надежность сети в условиях неблагоприятных условий.

- **Observability**. Получите понимание зависимостей между **services** и характером и потоком трафика **flow of traffic**  между ними, предоставляя возможность быстро выявлять проблемы.

- **Policy Enforcement**. Примените организационную политику к интерактивному взаимодействию между **services**, убедитесь, что политики доступа применяются и ресурсы распределены между потребителями **consumers**. Изменения политики вносятся путем настройки сетки, а не путем изменения кода приложения.

- **Service Identity and Security**. Предоставьте **services** в **mesh** с проверяемой идентичностью и предоставьте возможность защищать служебный трафик **protect service traffic**, поскольку он проходит по сетям различной степени надежности **trustability**.

В дополнение к этому поведению **Istio** разработан для расширяемости, чтобы удовлетворить разнообразные потребности деплоймента:

- **Platform Support**. **Istio** предназначен для работы в различных средах **environments**, в том числе в облачной, локальной, **Kubernetes**, **Mesos** и т. Д. Первоначально мы сосредоточены на Kubernetes, но и работаем над поддержкой других сред.

- **Integration and Customization**. Компонент реализации политики может быть расширен и настроен для интеграции с существующими решениями для **ACL**, **logging**, мониторинга, квот, аудита и многого другого.

Эти возможности значительно уменьшают связь между кодом приложения, базовой платформой и политикой. Эта уменьшенная связь не только упрощает реализацию **services**, но и упрощает **operators** перемещение деплоймента приложений между **environments** или в **new policy schemes**. В результате приложения становятся более переносимыми.

## Что такое трафик?

Использование модели управления трафиком **Istio’s traffic management** по существу не связывает масштабирование потока трафика и масштабирование инфраструктуры **traffic flow and infrastructure scaling**, позволяя операторам определять через **Pilot**, какие правила они хотят использовать для трафика, а не какие конкретные **pods/VMs** должны получать трафик - **Pilot** и интеллектуальные прокси-серверы **Envoy** следят за остальными. Так, например, вы можете указать через **Pilot**, что вы хотите, чтобы 5% трафика для конкретной службы переходило к **canary version** независимо от размера **canary deployment**, или отправляло трафик к конкретной версии в зависимости от содержимого запроса ,
