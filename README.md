# PA SDK Guide document

## How to update this document

1. `git clone https://github.com/pocketarena/pasdk.git`

2. Update document

3. `git add .`

4. `git commit -m "commit message here"`

5. `git push origin master`

6. Deploy it on the shell
```shell
./deploy.sh
```

7. Once finished the deploying document, the CANME will be reset. So, it needs to update the CNAME again in the setting, the target branch should be the `gh-pages`, `pasdkdoc.pocketarena.com`
