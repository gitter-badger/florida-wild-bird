# Create RRD file

```
#!/bin/bash

rrdtool create plant.rrd \
--start N --step 60 \
DS:moisture:GAUGE:300:0:1 \
RRA:MAX:0.5:5:3600
```

# Update value

```
rrdtool update plant.rrd "N:0"
```

# Create graph

```
#!/bin/bash

rrdtool graph mygraph.png -a PNG --title="Moisture" \
--vertical-label "Moisture level" \
'DEF:moisture=plant.rrd:moisture:MAX' \
'LINE1:moisture#ff0000:Moisture probe'
```