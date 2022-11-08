# Datapad Backend Assessment


## Introduction

Hi 👋

This project is created to help us to evaluate the candidates who are in application or evaluation process.

We mostly redirect candidates here during their technical assessment step. Still, you may also solve this
challenge and reach us with your application and solution attached as long as you think that you're a good
fit for our open positions listed at [datapad.io/jobs](https://datapad.io/jobs).


## Our Application Process

The entire process takes 3-7 days depending on the candidate's availability:

1. Initial Meeting Call (15m, On the Phone)
2. **Technical Evaluation** `<!-- you are here`
3. Culture-Fit Assessment (45m)
4. Proposal


## Technical Assessment

### Task

- Complete the tasks which will satisfy the requirements that are included in scenario
- Bundle your technical solution in order to make it ready to review-friendly (open-sourcing it is an option)
- Notify us about your progress by sending an e-mail to `assessments@datapad.io`


### Scenario

Suppose that you're working for an e-commerce company and you needed to provide data to 3rd party tool. In
order to do that, you need to automate extracting few metrics from a data source*.

This 3rd party tool will consume data from the endpoint you've specified but you'll also need to implement
the tool's predefined metrics and custom protocol schema `(see API Schema below)`.

On the other hand, the data source may be changed time to time. Therefore, you'll need to read it from the
online source.


#### Data Source

- [Google Spreadsheets](https://docs.google.com/spreadsheets/d/1frVzuJCImzpP-zEhSrzuQGV0rUp3mFxV5OfG0z1UZYg/edit?usp=sharing)


#### Metrics

- Avg. Revenue by Brand
- Weekly Sessions
- Daily Conversion Rate % 
- Net Revenue of Each Customer


### Technical Expectations

#### Technology Stack Limitations

- Programming Language: JavaScript or TypeScript
- Runtime/Platform: [Deno](https://deno.land/)
- Revision Control System: Git
- Containerization: Docker


#### Requirements:

- Granular and frequent commits on Git.
- `master` and `development` branches, along with some revision tags.
- Configuration via Environment Variables.
- Containerization of the solution.
- A `README.md` that explains how to make it work.


### API Schema

#### Avg. Revenue by Brand

Request:

```http
GET /metrics?id=revenue&dimensions=brand&aggregate=avg
```

Response:

```http
{
  "metric": "revenue",
  "dimensions": ["brand"],
  "aggregation": "avg",
  "data": {
    "Nike": [
      {
        "value": "1.23"
      }
    ],
    "Samsung": [
      {
        "value": "2.00"
      }
    ],
    "Apple": [
      {
        "value": "3.00"
      }
    ]
  }
}
```

#### Weekly Sessions

Request:

```http
GET /metrics?id=sessions&dimensions=date.weeknum&aggregate=distinct
```

Response:

```http
{
  "metric": "sessions",
  "dimensions": ["date.weeknum"],
  "aggregation": "distinct",
  "data": {
    49: [
      {
        "value": "2342"
      }
    ],
    50: [
      {
        "value": "2322"
      }
    ],
    51: [
      {
        "value": "1643"
      }
    ],
    52: [
      {
        "value": "34"
      }
    ]
  }
}
```

#### Daily Conversion Date %

Request:

```http
GET /metrics?id=conversion&dimensions=date&aggregate=distinct
```

Response:

```http
{
  "metric": "conversion",
  "dimensions": ["date"],
  "aggregation": "distinct",
  "data": {
    "2020-10-09": [
      {
        "sessions": 100,
        "purchases": 10,
        "value": "10.00"
      }
    ],
    "2020-10-10": [
      {
        "sessions": 1000,
        "purchases": 250,
        "value": "25.00"
      }
    ]
  }
}
```

#### Net Revenue of Each Customer

Request:

```http
GET /metrics?id=net-revenue&dimensions=customer&aggregate=sum&filter.date.from=2020-09-10&filter.date.to=2020-09-15
```

Response:

```http
{
  "metric": "net-revenue",
  "dimensions": ["customer"],
  "aggregation": "sum",
  "filters": {
    "date": {
      "from": "2020-09-10",
      "to": "2020-09-15"
    }
  }
  "data": {
    "Tim": [
      {
        "value": "321.40"
      }
    ],
    "Jane": [
      {
        "value": "25.00"
      }
    ],
    "Alex": [
      {
        "value": "78.00"
      }
    ]
  }
}
```


### Questions

Don't hesitate to contact us on `assessments@datapad.io` whenever you need additional assistance.

### License

Licensed with Apache 2.0, see [LICENSE](LICENSE) file for details.
