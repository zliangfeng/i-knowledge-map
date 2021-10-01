# autocannon

## content

```bash
// simulates a high stress situation where 2500 unique visitors visit your website at the same time and their browsers on average make 4 pipelined requests per TCP connection sustained for 30 seconds.
autocannon -c 2500 -d 30 -p 4 http://HOST:PORT/benchmark
```
