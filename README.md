[![GitHub](https://img.shields.io/github/license/yicr/aws-rds-database-running-scheduler?style=flat-square)](https://github.com/yicr/aws-rds-database-running-scheduler/blob/main/LICENSE)
[![npm (scoped)](https://img.shields.io/npm/v/@gammarer/aws-rds-database-running-scheduler?style=flat-square)](https://www.npmjs.com/package/@gammarer/aws-rds-database-running-scheduler)
[![PyPI](https://img.shields.io/pypi/v/gammarer.aws-rds-database-running-scheduler?style=flat-square)](https://pypi.org/project/gammarer.aws-rds-database-running-scheduler/)
<!-- [![Nuget](https://img.shields.io/nuget/v/Gammarer.CDK.AWS.SecureFlowLogBucket?style=flat-square)](https://www.nuget.org/packages/Gammarer.CDK.AWS.SecureFlowLogBucket/)  -->
[![Sonatype Nexus (Releases)](https://img.shields.io/nexus/r/com.gammarer/aws-rds-database-running-scheduler?server=https%3A%2F%2Fs01.oss.sonatype.org%2F&style=flat-square)](https://s01.oss.sonatype.org/content/repositories/releases/com/gammarer/aws-rds-database-running-scheduler/)
[![GitHub Workflow Status (branch)](https://img.shields.io/github/actions/workflow/status/yicr/aws-rds-database-running-scheduler/release.yml?branch=main&label=release&style=flat-square)](https://github.com/yicr/aws-rds-database-running-scheduler/actions/workflows/release.yml)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/yicr/aws-rds-database-running-scheduler?sort=semver&style=flat-square)](https://github.com/yicr/aws-rds-database-running-scheduler/releases)

# AWS RDS Database Running Scheduler

This is an AWS CDK Construct to make RDS Database running schedule (only running while working hours(start/stop)).

## Fixed

- RDS Aurora Cluster
- RDS Instance

## Resources

This construct creating resource list.

- EventBridge Scheduler execution role
- EventBridge Scheduler

## Install

### TypeScript

```shell
npm install @gammarer/aws-rds-database-running-scheduler
# or
yarn add @gammarer/aws-rds-database-running-scheduler
```

### Python

```shell
pip install gammarer.aws-rds-database-running-scheduler
```

### Java

Add the following to pom.xml:

```xml
<dependency>
  <groupId>com.gammarer</groupId>
  <artifactId>aws-rds-database-running-scheduler</artifactId>
</dependency>
```

## Example

```typescript
import { RdsDatabaseRunningScheduler, Type } from '@gammarer/aws-rds-database-running-scheduler';

new RdsDatabaseRunningScheduler(stack, 'RdsDatabaseRunningScheduler', {
  type: Type.CLUSTER, // TYPE.CLUSTER or TYPE.INSTANCE
  identifiers: {
    ['db-cluster-1a']: { // cluster identirier
      startSchedule: {
        timezone: 'Asia/Tokyo',
        minute: '55',
        hour: '8',
        week: 'MON-FRI',
      },
      stopSchedule: {
        timezone: 'Asia/Tokyo',
        minute: '5',
        hour: '19',
        week: 'MON-FRI',
      },
    },
  },
})

```

## License

This project is licensed under the Apache-2.0 License.



