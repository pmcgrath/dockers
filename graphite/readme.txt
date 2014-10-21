To see carbon aggregator inclusion see sha a1d236a853ea5c2c813b44ea8b5ca9cb9ec62ace

docker build -t pmcg/graphite1:2.0 .

docker run -d -p 80:80 -p 8125:8125/udp -p 8126:8126 pmcg/graphite1:1.0 /usr/bin/supervisord
docker run -d -p 80:80 -p 8125:8125/udp -p 8126:8126 pmcg/graphite1:2.0 /usr/bin/supervisord

echo stats | nc localhost 8125								# Issue if running this on the host, where no issue if within the container or on another machine
echo counters | nc localhost 8125							# Issue if running this on the host, where no issue if within the container or on another machine
echo "mycount:1|c" | nc -w 1 -u localhost 8125


Info
https://github.com/hopsoft/docker-graphite-statsd
	Different way of building the container that avoids the stacking problem with aufs
http://crosbymichael.com/advanced-docker-volumes.html
	Under the hood
http://www.offermann.us/2013/12/tiny-docker-pieces-loosely-joined.html
	.
http://ijonas.com/devops-2/a-docker-container-folder-structure-thats-flexible-and-scales/
	.

