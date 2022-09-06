

### Download all links from list

```bash
cat list.txt | while read link; do wget $link; done
#or 
while read link; do wget $link; done < list.txt
```
### Extract url from open s3 bucket
```bash
url=https://3s-hrl.amazonaws.com/; curl $url | grep -oP '(?<=<Key>).*?(?=</Key>)' | awk '{print $url$1} | tee list.txt'
```
### extract members from LinkedIn company (FIrst, copy the raw data from your browser into raw.txt
```bash
cat raw.txt | grep 'org-people-profile-card__profile-title t-black lt-line-clamp lt-line-clamp--single-line ember-view' | cut -d '>' -f 2 | grep -v 'LinkedIn Member' | sort -u
```
