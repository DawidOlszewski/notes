# dd imagining

`sudo dd if=/dev/sdd status=progress | tee >(md5sum > /tmp/hashsum) | dd of=sr1.dd`