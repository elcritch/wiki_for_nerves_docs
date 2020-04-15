
## Tips on building Custom Systems 

### Checking size of custom image

    joevandyk>
        is there a way to see what's taking up space in the firmware 
        builds? Mine is 70 megabytes.. I'm curious what's taking up the space.

    jonjon>
        On your host, do `mix firmware.unpack` and it will unpack your 
        firmware file where you can checkout file sizes of dir and files 
        in it. 

    erauer>  1 day ago
        For custom systems, it is possible to see the relative size of 
        packages as well, [Buildroot - Graph Size](https://buildroot.org/downloads/manual/manual.html#graph-size).

