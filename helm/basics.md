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
