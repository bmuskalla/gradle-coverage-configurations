### Setup Jacoco code coverage on a multi-module project using configurations

```
$ ./gradlew :aggregator:codeCoverageReport
```

Collecting coverage data is handled for subprojects using
```
subprojects {
    apply plugin: 'jacoco-collect-coverage'
```

Specifing what should be covered in the report using the report part (see `aggregator`). This uses a contributed configuration named `coverageSource`
```
plugins {
    id 'jacoco-report-all'
}

dependencies {
    coverageSource project(":application")
    coverageSource project(":list")
}
```

Interesting bits are [the plugins hosted in `buildSrc`](/tree/master/buildSrc/src/main/java/com/example/jacoco/report) 

### Output

HTML report at `aggregator/build/reports/jacoco/codeCoverageReport/html/index.html`

XML report (sonarqube, coverall, codecov) at `aggregator/build/reports/jacoco/codeCoverageReport/codeCoverageReport.xml`
