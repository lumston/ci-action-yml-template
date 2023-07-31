# continuous-integration-action

An action for continuous integration.

## Inputs

- **GITHUB_TOKEN** (required): GitHub token to authenticate actions.
- **RUNTIME_VERSION** (default: node): The version of the runtime used for the application. Available options: 16, 18.
- **RUNTIME** (default: node): The runtime of the application. Available option: node.

### Testing Options

- **COVERAGE_PATH** (default: ./coverage/coverage-summary.json): Path to the coverage summary file.
  
### Sonarqube Options

- **SONAR_PROJECT_NAME** (required): The name of the Sonarqube project.
- **SONAR_HOST_URL** (required): The URL of the Sonarqube host.
- **SONARQUBE_TOKEN** (required): Token for Sonarqube authentication.
- **SONAR_LCOV_PATH** (default: ./coverage/lcov.info): Path to the Sonarqube coverage file in LCOV format.
- **MIN_COVERAGE_VALUE** (default: 95): Minimum required coverage value (integer).
- **MIN_BUGS_VALUE** (default: 0): Minimum number of allowed bugs (integer).
- **MIN_HOTSPOTS_VALUE** (default: 0): Minimum number of allowed hotspots (integer).
- **MIN_EFFORT_VALUE** (default: 60): Minimum technical debt in minutes (integer).

## Environment Variables

- **COVERAGE_VALUE**: Holds the coverage value obtained from the Sonarqube analysis.
- **BUGS_VALUE**: Holds the number of bugs found in the code.
- **HOTSPOTS_VALUE**: Holds the number of hotspots found in the code.
- **EFFORT_VALUE**: Holds the technical debt in minutes.

## Usage

```yaml
jobs:
  continuous_integration:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3
      - name: Continuous Integration
        uses: jsalazar/continuous-integration-action@v1
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          RUNTIME_VERSION: '16'
          RUNTIME: 'node'
          COVERAGE_PATH: './coverage/coverage-summary.json'
          SONAR_PROJECT_NAME: 'your-project-name'
          SONAR_HOST_URL: 'https://sonarqube.example.com'
          SONARQUBE_TOKEN: ${{ secrets.SONARQUBE_TOKEN }}
          SONAR_LCOV_PATH: './coverage/lcov.info'
          MIN_COVERAGE_VALUE: 95
          MIN_BUGS_VALUE: 0
          MIN_HOTSPOTS_VALUE: 0
          MIN_EFFORT_VALUE: 60
License
This code is licensed under the MIT License.

Contact
For any questions or feedback, please contact the author:

Name: jsalazar
GitHub: jsalazar