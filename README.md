# scsonify
seismic sonification tool within SeisComP

## What is this?
Scsonify is an addon to the whidely used SeisComP package for seismic data analysis, processing and aquisition.
The tool sonifies (makes data audible) using a simple data compression technique, making seismic data accessible to all, as well as providing new insights into the complexity of earthquakes.
## Features.
- Integrates seemlessly with in the SeisComP framework.
- Commandline driven with simple commands that can be adjusted according to user needs.
- Standrd filtering of data, using the builtin SeisComP filter syntax.
- Outputs resulting sonifications to a .wav file.
- Multiple data sources : choose from a whide selection of data sources provided by local or remote hosts
  - Realtime data (SeedLink protocol)
  - Archived data using the SeisComP Data Structure (SDS).
  - Fech data via FDSN webservices, supporting an array of data centers (GFZ, IRIS, local fdsnws server.)
- Easily set periods of interest using the timespan flag.
## Work in progress.
This is still very much a work in progress, and new features are being worked on, they include:
- Sonification of multiple stations in 3D space for a single event.
- Sonification of events based on event IDs.
- API for integrating with existing tools, such as scalert, for generating automated sonifications of events of interest.
- Visual output, such as spectrograms, map overlays and event information alongside the audio output.

## Installation and usage.
To install scsonify, there are a few things needed:
- The SeisComP software, version 4 or newer.
- Numpy
- Scipy.

to install the software, simply do the following:
```
- Download seiscomp from [Here](https://www.seiscomp.de/downloader/), or build it from source.
- Install NumPy and SciPy:
  -pip install numpy scipy
- git clone https://github.com/Donavin97/scsonify.git
- cd scsonify && cp scsonify ~/seiscomp/bin
or using github-cli:
- gh repo clone Donavin97/scsonify
- cd scsonify && cp scsonify ~/seiscomp/bin/
```

## Usage.
```
scsonify -h
```
```
Records:
  --record-driver-list       List all supported RecordStream drivers.
  -I [ --record-url ] arg    The RecordStream source URL. Format:
                             [service://]location[#type]. 'service' is the name
                             of the RecordStream driver which can be queried
                             with '--record-driver-list'. If 'service' is not
                             given, 'file://' is used and simply the name of a
                             miniSEED file can be given.
  --record-file arg          Specify a file as record source.
  --record-type arg          Specify a type for the records being read.

Time:
  -T [ --time-window ] arg   Time window of data to sonify in format
                             start_time~end_time, e.g.,
                             2023-10-01T00:00:00~2023-10-01T01:00:00

Output:
  -o [ --output-file ] arg   Specify file to write sonified seismic data to.

Input:
  --stream arg               Specify seismic stream to sonify

Processing:
  -S [ --speed-factor ] arg  Speed up factor to make seismic data audible:
                             (e.g., a factor of 100 will speed up the data 100
                             times).
  -f [ --filter ] arg        Specify filter to apply to seismic data
```
to apply scsonify on some data, use the following syntax:
```
scsonify -I fdsnws://service.iris.edu -T "2025-10-01 04:00~2025-10-01 05:00" -f "RMHP(10)>>ITAPER(30)>>BW(4,2,15)" -o output.wav -S 160 --stream OK.MORE.--.HHZ
```
This will sonify 1 hour of data from the MORE station of the OK network for 1 October between 04:00 and 05:00 (UTC).
All parameters of the script are fully adjustable, meaning the user can chose parameters according to there specific usecase.
The filters are also fully adjustable, you can add in any filter string supported by SeisComP.
#### Conclusion.
This work is provided as is to the comunity.
I hope this can be of use to scientists, who wish to explore seismic data processing in a different way.
## License
    Copyright (C) 2025  Donavin Liebgott

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU Affero General Public License as published
    by the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU Affero General Public License for more details.

    You should have received a copy of the GNU Affero General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
 
## Contribution and contact.
Any contributions or suggestions are welcomed by the comunity.
Contributions can be submitted via pull requests to this repository.
If you wish to contact me, an email can be sent to:
(donavinliebgott@gmail.com)
## Software links
You can find the software used by this repo in the following table.
| Software | link |
|--------|--------|------|
| SeisComP | (https://www.seiscomp.de/) |
| NumPy | (https:://www.numpy.org/) |
| SciPy | (https://www.scipy.org/) |
