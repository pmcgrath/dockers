sudo docker run -t -i -p ... bash


echo stats | nc localhost 8125								# Issue if running this on the host, where no issue if within the container or on another machine
echo counters | nc localhost 8125								# Issue if running this on the host, where no issue if within the container or on another machine
echo "mycount:1|c" | nc -w 1 -u localhost 8125

