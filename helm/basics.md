# Helm Chart Basics

* In Helm chart we can define the dependency helm charts, while installing the parent helm chart the dependencies are downloaded from repos and stored in charts/ folder. We can also manually download and put the chart.tgz in charts/ folder
  * Defining the dependency helm chart in parent Charts.yaml
    ```
    # parentchart/Chart.yaml
    apiVesrion: v2
    name: parentchart
    version: 1.0.0
    dependencies:
      - name: apache
        version: 1.2.3
        repository: https://example.com/charts
      - name: mysql
        version: 3.2.1
        repository: https://another.example.com/charts
    ```
  * we can use "alias" option to rename the chart and store in /charts folder
    ```
    # parentchart/Chart.yaml
    apiVesrion: v2
    name: parentchart
    version: 1.0.0
    dependencies:
      - name: subchart
        repository: http://localhost:10191
        version: 0.1.0
        alias: new-subchart-1
      - name: subchart
        repository: http://localhost:10191
        version: 0.1.0
        alias: new-subchart-2
      - name: subchart
        repository: http://localhost:10191
        version: 0.1.0
    ```
  * we can use "tags" and "condition" option to control the installation of dependency charts. condition has higher preference than tags.The first condition path     that exists wins and subsequent ones for that chart are ignored. If the "condition" values are not defined in the values.yaml, then the defined "condition"       has no effect. Tags and conditions values must be set in the top parent's values.The tags: key in values must be a top level key. Globals and nested tags:         tables are not currently supported.
    ```
    # parentchart/Chart.yaml
    dependencies:
      - name: subchart1
        repository: http://localhost:10191
        version: 0.1.0
        condition: subchart1.enabled, global.subchart1.enabled
        tags:
          - front-end
          - subchart1
      - name: subchart2
        repository: http://localhost:10191
        version: 0.1.0
        condition: subchart2.enabled,global.subchart2.enabled
        tags:
          - back-end
          - subchart2
    ```
    ```
    # parentchart/values.yaml

    subchart2:
      enabled: true
    tags:
      front-end: false
      back-end: true
    ```
  * The --set parameter can be used as usual to alter tag and condition values.
    ```
    helm install --set tags.front-end=true --set subchart2.enabled=false
    ```
