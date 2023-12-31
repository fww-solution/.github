# FWW (Fly Without Wings) Solution
## Description
This is a solution for the FWW (Fly Without Wings) problem. The problem is to find the shortest path from a given source to a given destination in a graph. The graph is given as a list of edges. The solution is implemented in Go and use Bonita BPMN 2.0 engine to execute the process.

## Sequence Diagram

### Passenger Sequence Diagram

![Alt text](./profile/image-2.png)

### Booking Sequence Diagram

![Alt text](./profile/image-3.png)

### Payment Sequence Diagram

![Alt text](./profile/image-4.png)

### Redeem Ticket Sequence Diagram

![Alt text](./profile/image-5.png)

## System Design

![Alt text](./profile/image-6.png)

## ERD

![Alt text](./profile/image.png)

## API Documentation

To view the API documentation, please run the application and go to the following URL:

### Postman Collection

[https://www.getpostman.com/collections](https://www.getpostman.com/collections/4625022-61aa55ac-dd32-4406-9cc8-f9e3134d80d0)

### Swagger

[https://fww-solution.github.io/.github/](https://fww-solution.github.io/.github/)

## How to run

## Repositories

All repositories are hosted on GitHub. The following is the list of repositories:

- [https://github.com/fww-solution/fww-wrapper.git](https://github.com/fww-solution/fww-wrapper.git)

- [https://github.com/fww-solution/fww-core.git](https://github.com/fww-solution/fww-core.git)

- [https://github.com/fww-solution/bpm-wrapper.git](https://github.com/fww-solution/bpm-wrapper.git)

- [https://github.com/fww-solution/bpm-rintime.git](https://github.com/fww-solution/bpm-rintime.git)

### Prerequisites

(run locally)
Docker already installed

Clone sre repository

```bash
git clone https://github.com/fww-solution/fww-sre.git
```

```bash
cd deploy/local
docker-compose up -d
```

### Run

## How to test

### Security Test

To perform security test at [fww-core service](https://github.com/fww-solution/fww-core.git), please run the following command:

```bash
make scan
```

### Unit Test

To perform unit test at [fww-core service](https://github.com/fww-solution/fww-core.git), please run the following command:

```bash
make test
```

### E2E Test

To perform E2E we need to run the following command:

[postman collection](./fww_soution.postman_collection.json)

[postman environment](./fww_development.postman_environment.json)

Install newman postman

```bash
npm install -g newman
```

Run the following command:

```bash
newman run fww_solution.postman_collection.json -e fww_development.postman_environment.json
```

example output:

![Alt text](./profile/image-1.png)

### Load Test

We are using [hey](https://github.com/rakyll/hey) to perform load test. To install hey, please run the following command:

```bash
hey -H "Content-Type: application/json" -m POST -n 172 -c 50 -d '{
  "flight_id": 2,
  "user_id": 2,
  "book_details": [
    {
      "passanger_id": 2,
      "class": "Economy",
      "baggage": 20,
      "seat_number": "12A"
    },
    {
      "passanger_id": 3,
      "class": "Economy",
      "baggage": 30,
      "seat_number": "1B"
    }
  ]
}' http://{URL}/api/v1/booking
```

output example:

![Alt text](./profile/image-8.png)


## How to deploy

### Docker Local

To deploy the application locally, please run the following command:

clone the repository

```bash
git clone https://github.com/fww-solution/fww-sre.git

```bash
cd deploy/local && make deploy-local
```

## How to monitor

To monitor logs, we using grafana and prometheus. To access grafana, please go to the following URL:

```bash

http://(PUBLIC_URL):8084

```

example output:

![Alt text](./profile/image-7.png)
