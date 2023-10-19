name: Java CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up JDK 11
      uses: actions/setup-java@v3
      with:
        java-version: '11'
        distribution: 'temurin'
        # cache: maven
    - name: FireFlink suite execution
      run: java -jar fireflink-action-1.0.0.jar ${{secrets.FIREFLINK_URL}} ${{secrets.FIREFLINK_SUITE_ID}} ${{secrets.FIREFLINK_TOKEN}} ${{secrets.FIREFLINK_PROJECT_TYPE}}
