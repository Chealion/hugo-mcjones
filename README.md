Both the home for my docs theme and my docs content that powers https://mcjones.ca

Gather any Bear notes I have tagged as public, put them into the  docs.

```
cd ~/src/hugo-mcjones
python bear_export_sync.py --skipImport --out /tmp/Bear/
cp /tmp/Bear/public/* content/docs/
git add content/docs
git commit -m "Content Update $(date)"
hugo
rsync -avzh public/ mcjones.ca:mcjones
```

## Images

https://icons.getbootstrap.com/
