fastapi-satella-metrics
=====================
[![Build Status](https://travis-ci.com/Dronehub/fastapi-satella-metrics.svg)](https://travis-ci.com/Dronehub/fastapi-satella-metrics)
[![Test Coverage](https://api.codeclimate.com/v1/badges/34b392b61482d98ad3f0/test_coverage)](https://codeclimate.com/github/Dronehub/fastapi-satella-metrics/test_coverage)
[![Code Climate](https://codeclimate.com/github/Dronehub/fastapi-satella-metrics/badges/gpa.svg)](https://codeclimate.com/github/Dronehub/fastapi-satella-metrics)
[![Issue Count](https://codeclimate.com/github/Dronehub/fastapi-satella-metrics/badges/issue_count.svg)](https://codeclimate.com/github/Dronehub/fastapi-satella-metrics)
[![PyPI](https://img.shields.io/pypi/pyversions/fastapi-satella-metrics.svg)](https://pypi.python.org/pypi/fastapi-satella-metrics)
[![PyPI version](https://badge.fury.io/py/fastapi-satella-metrics.svg)](https://badge.fury.io/py/fastapi-satella-metrics)
[![PyPI](https://img.shields.io/pypi/implementation/fastapi-satella-metrics.svg)](https://pypi.python.org/pypi/fastapi-satella-metrics)
[![License](https://img.shields.io/pypi/l/fastapi-satella-metrics)](https://github.com/Dronehub/fastapi-satella-metrics)

fastapi-satella-metrics is an application to seamlessly measure your FastAPI
application using Satella's metrics.

Example use:

```python
import fastapi
from fastapi_satella_metrics import SatellaMetricsMiddleware
app = fastapi.FastAPI()
app.add_middleware(SatellaMetricsMiddleware)
```

And to launch a Prometheus exporter use the following snippet:

```python
from satella.instrumentation.metrics.exporters import PrometheusHTTPExporterThread
phet = PrometheusHTTPExporterThread('0.0.0.0', 8080, {'service_name': 'my_service'})
phet.start()
```

Or, if you desire to export your metrics within FastAPI, just use:

```python
import fastapi
from fastapi_satella_metrics.prometheus_exporter import PrometheusExporter
app = fastapi.FastAPI()
app.include_router(PrometheusExporter({'service_name': 'my_service'}))
```
