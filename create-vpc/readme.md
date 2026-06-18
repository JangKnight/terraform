# Setup

## Terraform block 

```tf
  terraform {
    required_providers {
      aws = {
        source = "hashicorp/aws"
        version = "~>5.0"
      }
    }
  }
```

## Provider block

```tf
  provider "aws" {
    region = "us-east-1"
  }
```

## VPC

```tf
  resource "aws_vpc" "main" {
    cidr_block = "10.0.0.0/16"
  }
```

## Subnets (Public and Private)

```tf
  resource "aws_subnet" "public" {
    vpc_id            = aws_vpc.main.id
    cidr_block        = "10.0.0.0/24"
  }

  resource "aws_subnet" "private" {
    vpc_id            = aws_vpc.main.id
    cidr_block        = "10.0.1.0/24"
  }
```

## Internet Gateway


```tf
  resource "aws_internet_gateway" "igw" {
    vpc_id = aws_vpc.main.id
  }
```

## Route Tables

```tf
  resource "aws_route_table" "public_rt" {
    vpc_id = aws_vpc.main.id

    route {
      cidr_block = "0.0.0/0"
      gateway_id = aws_internet_gateway.igw.id
    }
  }
```

## Route Table Associations
```tf
  resource "aws_route_table_association" "public_rt_assoc" {
    subnet_id      = aws_subnet.public.id
    route_table_id = aws_route_table.public_rt.id
  }
```
