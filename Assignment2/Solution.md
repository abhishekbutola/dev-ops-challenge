# Assignment 2

We want to gather some basic statistics for our security team. They want to know the top 8 IP addresses that hit our web servers.

Your task will be the following:
Implement a script (use any language you want) to get the top 8 IP addresses out of an existing log file
Save your script with no file extension
It has to be an executable file
there is no need to use arguments
The output format will be the following:(8 lines - top saw IP addresses by the number of hits):

<ip_address>`<space>`<number_of_hits>

A real example output would look like this:

$ count

92.6.41.236 22

186.248.72.9 19

81.243.137.36 18

217.118.78.16 15

213.118.39.51 15

93.146.139.64 14

80.116.15.0 14

186.213.159.176 11

# Solution

The IP are to extracted from the log file. Since the IP is at every line we can split individual lines and extract IP from it.

    lines = lc.splitlines()

we can get the IP pattern and match it from the split lines

    ip_pattern = r'\b(\d{1,3}\.)(\d{1,3}\.)(\d{1,3}\.)(\d{1,3})\b'

Then match the pattern in the split lines

    matches = re.findall(ip_pattern, line)

join to combine IP and extend it in a list

    ip_addresses = [''.join(match) for match in matches]

    ip_list.extend(ip_addresses)

count the occurance of each item in list uniquely

    ip_counter = Counter(ip_list)

print the occurance of each ip

    print(f"{ip} {occurrence}")
