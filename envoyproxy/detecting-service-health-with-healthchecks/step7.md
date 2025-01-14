В отличие от активной проверки работоспособности **health checking**, обнаружение выбросов *Outlier Detection*  (иногда называемое пассивной проверкой работоспособности **passive health checking**) использует ответы от реальных запросов, чтобы определить, исправна ли конечная точка **endpoint is healthy**. После удаления конечной точки **endpoint is removed** Envoy использует подход, основанный на тайм-ауте, для повторной вставки, при котором неработоспособные хосты повторно добавляются в кластер после настраиваемого интервала. При каждом последующем удалении интервал увеличивается, поэтому постоянно неработоспособная конечная точка **unhealthy endpoint** наносит минимальный ущерб пользовательскому трафику **user traffic**.

Как и проверки работоспособности **health checks**, обнаружение выбросов настраивается для каждого кластера. Эта конфигурация удаляет хост на 30 секунд, когда он возвращает 3 раз последовательно **5xx errors**:

Откройте файл `envoy1.yaml`{{open}} и добавьте следующую конфигурацию:

<pre class="file" data-filename="envoy1.yaml" data-target="append">
    outlier_detection:
        consecutive_5xx: "3"
        base_ejection_time: "30s"
</pre>

Ключевые поля **key fields**:

* **sequence_5xx**: если **upstream host** возвращает некоторое количество последовательных 5xx, он будет удален. 
Обратите внимание, что в этом случае **5xx** означает фактический код ответа **5xx** или событие, которое заставит маршрутизатор HTTP вернуть его от имени потока **upstream’s behalf (reset, connection failure, etc.)**.

* **base_ejection_time**: базовое время, в течение которого хост **ejected**. Реальное время равно базовому времени, умноженному на количество раз, когда хост был удален. По умолчанию **30000ms or 30s**.

Более подробную информацию об API можно найти в [Envoy documentation](https://www.envoyproxy.io/docs/envoy/latest/api-v2/api/v2/cluster/outlier_detection.proto).

См. [Обзор архитектуры](https://www.envoyproxy.io/docs/envoy/latest/intro/arch_overview/upstream/outlier#arch-overview-outlier-detection)для получения дополнительной информации об обнаружении выбросов **outlier detection**.

```
{
  "consecutive_5xx": "{...}",
  "interval": "{...}",
  "base_ejection_time": "{...}",
  "max_ejection_percent": "{...}",
  "enforcing_consecutive_5xx": "{...}",
  "enforcing_success_rate": "{...}",
  "success_rate_minimum_hosts": "{...}",
  "success_rate_request_volume": "{...}",
  "success_rate_stdev_factor": "{...}",
  "consecutive_gateway_failure": "{...}",
  "enforcing_consecutive_gateway_failure": "{...}",
  "split_external_local_origin_errors": "...",
  "consecutive_local_origin_failure": "{...}",
  "enforcing_consecutive_local_origin_failure": "{...}",
  "enforcing_local_origin_success_rate": "{...}",
  "failure_percentage_threshold": "{...}",
  "enforcing_failure_percentage": "{...}",
  "enforcing_failure_percentage_local_origin": "{...}",
  "failure_percentage_minimum_hosts": "{...}",
  "failure_percentage_request_volume": "{...}"
}
```
