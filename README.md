# Network tools

These are a couple of small, single-purpose network testing tools that I've found useful to write while setting up and configuring wireless networks.

## access-point-identify

If you configure multiple access points with the same SSID, wireless devices will (in theory) roam between them, depending on which access point provides the strongest signal. A simple example is a router that provides both 2.4GHz and 5GHz networks with the same SSID, but it can get more complex with multiple access points.

When testing multi-access point setups, there's no obvious way to determine which access point you're connected to. This script lets you see the name of the current access point, and displays the current and maximum transmit rates supported.

### Usage

To set up, find the BSSIDs for each access point on your network and add them to `ap-config.yaml` along with the name. If you don't know the BSSIDs, check the labels on the back of the router, or run the script to list it.

Once you're set up, run the script:

	$ perl access-point-identify
	Connected to access point 'Linksys 1, 5GHz'
	Transmit rate is 264/1300 Mbps
	
	$ perl access-point-identify
	Connected to access point 'Asus 1, 2.4GHz'
	Transmit rate is 130/217 Mbps
	
Running the script with `watch` can be useful to run the script repeatedly while walking around the house:

	watch perl access-point-identify

## throughput - network benchmarking

Work out how fast your WiFi really is, in every room.
`throughput` lets you walk from room to room, and record network transfer speeds.

Record the name of each location you test from, and review everything from a CSV file later.

Requires two computers (or some kind of device with a network share) to do the benchmarking.

### Setup

Install any missing perl modules:

	cpan Text::CSV

Wire a second computer up to the network you're testing, and create a network share on it.
Mount that share on your main computer, and change the `dest_path` field in the config file. The testing writes files of varying size to the network share.

### Example usage

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
