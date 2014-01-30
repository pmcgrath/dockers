sudo docker run -t -i -p ... bash
sudo docker run -t -i -p 80:80 -p 8125:8125/udp -p 8126:8126 nmcg/g1 bash


echo stats | nc localhost 8125								# Issue if running this on the host, where no issue if within the container or on another machine
echo counters | nc localhost 8125								# Issue if running this on the host, where no issue if within the container or on another machine
echo "mycount:1|c" | nc -w 1 -u localhost 8125

