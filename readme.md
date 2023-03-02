

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
## extract members from LinkedIn company (First, copy the raw data from your browser into raw.txt)
```bash
cat raw.txt | grep 'org-people-profile-card__profile-title t-black lt-line-clamp lt-line-clamp--single-line ember-view' | cut -d '>' -f 2 | grep -v 'LinkedIn Member' | sort -u
```

## Download all videos from INE page
click all videos in INE page filter network traffic for media and string "1.ts"
```js
for (let i = 1; i <= document.getElementsByClassName('btn btn--secondary level__btn-sub').length; i++) {
    document.getElementsByClassName('btn btn--secondary level__btn-sub')[i].click();await new Promise(r => setTimeout(r, 5000));
}
```
tahn, in network pange, right click and select "save all as HAR file"
in terminal run 
```bash  
cat my.ine.com.har | grep jwpsrv | grep mp4-1.ts | grep url | cut -d'"' -f4 | sed -s 's/-1.ts//g'
```

## find company user names from pdf files
requirements: go-dork, exiftool
```bash
go-dork -q "site:target.com ext:pdf" -p 10 -s >> list.txt
wget -i list.txt
for i in *.pdf; do exiftool -creator -author  $i; done | cut -d: -f2 | sort -uf | grep -v ® 

```
