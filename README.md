# Network benchmarking

Set up a target computer that's wired to the router. Run this on a second machine, and the benchmark will copy a file over the network, and time how long it takes.

You can perform multiple runs from different locations, and will be prompted for a short description of your location on each run. Location and throughput speeds will be recorded in a CVS file for further prodding.

# Example usage

	$ perl throughput
	Enter test name: 5ghz test
	Writing to '5ghz test.csv'
	Approximate throughput is 16.60 MB/s
	Enter location name: lounge
	Throughputs for lounge (3 runs) are: 10.90 MB/s 13.22 MB/s 14.15 MB/s
	Average: 12.76 MB/s
	Enter location name: bedroom
	Throughputs for bedroom (3 runs) are: 15.14 MB/s 14.96 MB/s 17.68 MB/s
	Average: 15.93 MB/s
	
This will also write all the results `5ghz test.csv`.
