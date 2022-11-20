### `worker_processes` directive

Tells nginx how many processes or instances to fire-up when starting.
value `auto`: is not a default value, sets it to the number of the CPU cores available in the system

#### # Useful Commands

- `nproc` give a number of core of the CPU in the system
- `lscpu` give a detail about the processor in the system

<hr>

### `events.worker_connections` directive

Tells the processes how many request can be serve simultaneously. <br>
If we have 2 worker_processes and you have worker_connections set to 1024, that is equal to 2048 concurrent request
