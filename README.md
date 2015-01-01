# Network benchmarking

Work out how fast your WiFi really is, in every room.
`throughput` lets you walk from room to room, and record network transfer speeds.

Record the name of each location you test from, and review everything from a CSV file later.

Requires two computers (or some kind of device with a network share) to do the benchmarking.

# Setup

Install any missing perl modules:

	cpan Text::CSV

Wire a second computer up to the network you're testing, and create a network share on it.
Mount that share on your main computer, and change the `dest_path` field in the config file. The testing writes files of varying size to the network share.

# Example usage

	$ perl throughput
	Enter test name: 5GHz-range
	Writing to '5GHz-range.csv'
	Approximate throughput is 16.60 MB/s
	Enter location name: lounge
	Throughputs for lounge (3 runs) are: 10.90 MB/s 13.22 MB/s 14.15 MB/s
	Average: 12.76 MB/s
	Enter location name: bedroom
	Throughputs for bedroom (3 runs) are: 15.14 MB/s 14.96 MB/s 17.68 MB/s
	Average: 15.93 MB/s
	
Results are written to `5GHz-range.csv`.
