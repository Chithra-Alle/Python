|Function	|Description|	Example|
|:------:|:----:|:---------:|
|time.time()|	Returns the current time in seconds since the epoch.|	python <br> import time <br> print(time.time()) # Returns current time in seconds since epoch|
|time.sleep(seconds)|	Suspends execution for a given number of seconds. |	python <br> import time <br> print("Start...") <br> time.sleep(2) <br> print("End after 2 seconds")|
|time.localtime([secs])|	Converts a timestamp to a struct_time in local time. |	python <br> import time <br> print(time.localtime()) # Local time from the current timestamp|
|time.gmtime([secs])|	Converts a timestamp to a struct_time in UTC. |	python <br> import time <br> print(time.gmtime()) # UTC time from the current timestamp|
|time.strftime(format, t)	|Converts a struct_time or current time to a string according to the format. |	python <br> import time <br> print(time.strftime("%Y-%m-%d %H:%M:%S")) # Format current time|
|time.strptime(string, format)|	Parses a string into a struct_time based on the given format. |	python <br> import time <br> parsed_time = time.strptime("2025-02-13 14:30:00", "%Y-%m-%d %H:%M:%S") <br> print(parsed_time)|
|time.mktime(t)|	Converts a struct_time to a timestamp (seconds since the epoch).	| python <br> import time <br> current_time = time.localtime() <br> print(time.mktime(current_time))|
|time.perf_counter()|	Returns a high-resolution performance counter for measuring time. |	python <br> import time <br> start = time.perf_counter() <br> # Some task <br> end = time.perf_counter() <br> print(f"Elapsed time: {end - start} seconds")|
|time.process_time()|	Returns the CPU time used by the current process. |	python <br> import time <br> start = time.process_time() <br> # Some CPU-bound task <br> end = time.process_time() <br> print(f"CPU time: {end - start} seconds")|
### Key Points:
- time.time() gives the timestamp (seconds since the epoch).
- time.sleep(seconds) is used to pause program execution.
- time.localtime() converts the timestamp into local time (a struct_time object).
- time.gmtime() converts the timestamp into UTC time (a struct_time object).
- time.strftime() is used to format time as a string.
- time.strptime() is used to parse a time string into a struct_time object.
- time.mktime() converts a struct_time object back into a timestamp.
- time.perf_counter() provides high-resolution time for performance measurements.
- time.process_time() measures CPU time for the current process.
