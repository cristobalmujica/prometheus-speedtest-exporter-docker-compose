# Speedtest.net exporter for Prometheus
Speedtest.net offcial cli app - Prometheus Exporter

This is a small exporter built to allow Prometheus to scrape internet speedtests done with the official cli app from speedtest.net.

There are other exporters out there but they use a community done speedtest client that doesn't give accurate results

## Environment



## Puting it all together

* Install speedtest client using instructions above

* Add relevant config to prometheus.yml. Example:
```
scrape_configs:
  - job_name: 'Speedtest'
    scrape_interval: 5m
    scrape_timeout: 1m
    metrics_path: /metrics
    params:
      script: [speedtest]
    static_configs:
      - targets:
        - speedtest-exporter:9469
```

* Restart Prometheus to reload new config

## Grafana

Import JSON Dashboard

'''
{
  "annotations": {
    "list": [
      {
        "builtIn": 1,
        "datasource": {
          "type": "datasource",
          "uid": "grafana"
        },
        "enable": true,
        "hide": true,
        "iconColor": "rgba(0, 211, 255, 1)",
        "name": "Annotations & Alerts",
        "type": "dashboard"
      }
    ]
  },
  "description": "Dashboard for my Speedtest exporter",
  "editable": true,
  "fiscalYearStartMonth": 0,
  "gnetId": 11988,
  "graphTooltip": 0,
  "id": 1,
  "links": [],
  "liveNow": false,
  "panels": [
    {
      "aliasColors": {
        "Download Speed": "dark-green"
      },
      "bars": false,
      "dashLength": 10,
      "dashes": false,
      "datasource": {
        "type": "prometheus",
        "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
      },
      "fieldConfig": {
        "defaults": {
          "links": []
        },
        "overrides": []
      },
      "fill": 1,
      "fillGradient": 10,
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 0
      },
      "hiddenSeries": false,
      "id": 9,
      "legend": {
        "alignAsTable": true,
        "avg": true,
        "current": true,
        "max": true,
        "min": true,
        "show": true,
        "total": false,
        "values": true
      },
      "lines": true,
      "linewidth": 1,
      "nullPointMode": "connected",
      "options": {
        "alertThreshold": true
      },
      "percentage": false,
      "pluginVersion": "10.2.0",
      "pointradius": 2,
      "points": false,
      "renderer": "flot",
      "seriesOverrides": [],
      "spaceLength": 10,
      "stack": false,
      "steppedLine": false,
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
          },
          "editorMode": "code",
          "expr": "speedtest_download_speed_bytes*8",
          "hide": false,
          "interval": "",
          "legendFormat": "Download Speed",
          "range": true,
          "refId": "A"
        }
      ],
      "thresholds": [],
      "timeRegions": [],
      "title": "Downstream",
      "tooltip": {
        "shared": true,
        "sort": 0,
        "value_type": "individual"
      },
      "type": "graph",
      "xaxis": {
        "mode": "time",
        "show": true,
        "values": []
      },
      "yaxes": [
        {
          "$$hashKey": "object:393",
          "format": "bps",
          "label": "Speed",
          "logBase": 1,
          "min": "0",
          "show": true
        },
        {
          "$$hashKey": "object:394",
          "format": "short",
          "logBase": 1,
          "show": true
        }
      ],
      "yaxis": {
        "align": false
      }
    },
    {
      "aliasColors": {
        "Upload Speed": "dark-orange"
      },
      "bars": false,
      "dashLength": 10,
      "dashes": false,
      "datasource": {
        "type": "prometheus",
        "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
      },
      "fieldConfig": {
        "defaults": {
          "links": []
        },
        "overrides": []
      },
      "fill": 1,
      "fillGradient": 10,
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 0
      },
      "hiddenSeries": false,
      "id": 8,
      "legend": {
        "alignAsTable": true,
        "avg": true,
        "current": true,
        "max": true,
        "min": true,
        "show": true,
        "total": false,
        "values": true
      },
      "lines": true,
      "linewidth": 1,
      "nullPointMode": "connected",
      "options": {
        "alertThreshold": true
      },
      "percentage": false,
      "pluginVersion": "10.2.0",
      "pointradius": 2,
      "points": false,
      "renderer": "flot",
      "seriesOverrides": [],
      "spaceLength": 10,
      "stack": false,
      "steppedLine": false,
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
          },
          "editorMode": "code",
          "expr": "speedtest_upload_speed_bytes*8",
          "legendFormat": "Upload Speed",
          "range": true,
          "refId": "A"
        }
      ],
      "thresholds": [],
      "timeRegions": [],
      "title": "Upstream",
      "tooltip": {
        "shared": true,
        "sort": 0,
        "value_type": "individual"
      },
      "type": "graph",
      "xaxis": {
        "mode": "time",
        "show": true,
        "values": []
      },
      "yaxes": [
        {
          "$$hashKey": "object:466",
          "format": "bps",
          "label": "Speed",
          "logBase": 1,
          "min": "0",
          "show": true
        },
        {
          "$$hashKey": "object:467",
          "format": "short",
          "logBase": 1,
          "show": true
        }
      ],
      "yaxis": {
        "align": false
      }
    },
    {
      "aliasColors": {
        "Jitter": "dark-purple"
      },
      "bars": false,
      "dashLength": 10,
      "dashes": false,
      "datasource": {
        "type": "prometheus",
        "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
      },
      "description": "",
      "fieldConfig": {
        "defaults": {
          "links": []
        },
        "overrides": []
      },
      "fill": 5,
      "fillGradient": 10,
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 0,
        "y": 8
      },
      "hiddenSeries": false,
      "id": 2,
      "legend": {
        "alignAsTable": true,
        "avg": true,
        "current": true,
        "max": true,
        "min": true,
        "show": true,
        "total": false,
        "values": true
      },
      "lines": true,
      "linewidth": 2,
      "nullPointMode": "connected",
      "options": {
        "alertThreshold": true
      },
      "percentage": false,
      "pluginVersion": "10.2.0",
      "pointradius": 2,
      "points": false,
      "renderer": "flot",
      "seriesOverrides": [],
      "spaceLength": 10,
      "stack": false,
      "steppedLine": false,
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
          },
          "editorMode": "code",
          "expr": "speedtest_jitter_seconds",
          "format": "time_series",
          "instant": false,
          "intervalFactor": 1,
          "legendFormat": "Jitter",
          "refId": "A"
        }
      ],
      "thresholds": [],
      "timeRegions": [],
      "title": "Jitter",
      "tooltip": {
        "shared": true,
        "sort": 0,
        "value_type": "individual"
      },
      "type": "graph",
      "xaxis": {
        "mode": "time",
        "show": true,
        "values": []
      },
      "yaxes": [
        {
          "$$hashKey": "object:549",
          "format": "ms",
          "label": "",
          "logBase": 1,
          "min": "0",
          "show": true
        },
        {
          "$$hashKey": "object:550",
          "format": "short",
          "logBase": 1,
          "show": true
        }
      ],
      "yaxis": {
        "align": false
      }
    },
    {
      "aliasColors": {
        "Latency": "dark-yellow"
      },
      "bars": false,
      "dashLength": 10,
      "dashes": false,
      "datasource": {
        "type": "prometheus",
        "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
      },
      "fieldConfig": {
        "defaults": {
          "links": []
        },
        "overrides": []
      },
      "fill": 5,
      "fillGradient": 10,
      "gridPos": {
        "h": 8,
        "w": 12,
        "x": 12,
        "y": 8
      },
      "hiddenSeries": false,
      "id": 4,
      "legend": {
        "alignAsTable": true,
        "avg": true,
        "current": true,
        "hideEmpty": false,
        "max": true,
        "min": true,
        "rightSide": false,
        "show": true,
        "total": false,
        "values": true
      },
      "lines": true,
      "linewidth": 1,
      "links": [],
      "nullPointMode": "connected",
      "options": {
        "alertThreshold": true
      },
      "percentage": false,
      "pluginVersion": "10.2.0",
      "pointradius": 0.5,
      "points": false,
      "renderer": "flot",
      "seriesOverrides": [],
      "spaceLength": 10,
      "stack": false,
      "steppedLine": false,
      "targets": [
        {
          "datasource": {
            "type": "prometheus",
            "uid": "ddb02a53-e007-4341-b7ca-d770d08a7fdc"
          },
          "expr": "speedtest_latency_seconds",
          "legendFormat": "Latency",
          "refId": "A"
        }
      ],
      "thresholds": [],
      "timeRegions": [],
      "title": "Latency",
      "tooltip": {
        "shared": true,
        "sort": 0,
        "value_type": "individual"
      },
      "type": "graph",
      "xaxis": {
        "mode": "time",
        "show": true,
        "values": []
      },
      "yaxes": [
        {
          "format": "ms",
          "logBase": 1,
          "min": "0",
          "show": true
        },
        {
          "format": "short",
          "logBase": 1,
          "show": false
        }
      ],
      "yaxis": {
        "align": false
      }
    }
  ],
  "refresh": "5s",
  "schemaVersion": 38,
  "tags": [],
  "templating": {
    "list": []
  },
  "time": {
    "from": "now-6h",
    "to": "now"
  },
  "timepicker": {},
  "timezone": "",
  "title": "Speedtest Exporter",
  "uid": "MBmaYd9Wk",
  "version": 12,
  "weekStart": ""
}

'''

My grafana dashboard is available [here](https://grafana.com/grafana/dashboards/11988/)

Or the speedtest-exporter.json present in this repo can be used instead.
