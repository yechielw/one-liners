
-------------------


## Download all links from list

```bash
cat list.txt | while read link; do wget $link; done
#or 
while read link; do wget $link; done < list.txt
```
## Extract url from open s3 bucket
```bash
url=https://3s-hrl.amazonaws.com/; curl $url | grep -oP '(?<=<Key>).*?(?=</Key>)' | awk '{print $url$1} | tee list.txt'
```
