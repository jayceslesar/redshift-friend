# redshift-friend
At its core, this project aims to make Redshift more friendly through two main tools.

## Schema Migrations
Schema migrations can be a pain in Redshift, and can take down your cluster for an indefinite amount of time
if you do not do it properly. This project builds off of [alembic](https://github.com/sqlalchemy/alembic), with some added
requirements to make migrations as seamless as possible, with the hopes of minimizing cluster downtime.

## Redshift Doctor
Redshift is a beast if not maintained correctly. There are tools in the Redshift console that often supply incorrect information
on how to alter tables and databases in your cluster that result in high bills, poor performance, unhappy end-users, and even unhappier developers. This tool will walk you through picking distribution styles, sort keys, and compression encodings on new and existing tables by a suite of CLI prompts and even analyzing data directly in your cluster.


### How?
There are two main components that make all the magic described above happen:
1: IAM role with read access to your cluster's system tables, in order to properly analyze and diagnose (administrator of your AWS account/cluster will need to create the credentials with the boto3 Redshift api)
2: ECS Task with permissions to query against your cluster. How you invoke it is up to you

All of this will be able to be deployed within a VPC through the CDK through a few custom constructs to ensure you own everything :D

No promises of this ever being a real project and/or live, but one can dream.
