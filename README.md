"# test-deploy-cpanel" 
on:
  push:
    branches: [ ftp ]

name: 🚀 Deploy website on push
jobs:
  web-deploy:
    name: 🎉 Deploy
    runs-on: ubuntu-latest
    steps:
    - name: 🚚 Get latest code
      uses: actions/checkout@v2
    
    - name: 📂 Sync files
      uses: SamKirkland/FTP-Deploy-Action@4.3.0
      with:
        server: ${{ secrets.FTP_SERVER }}
        username: ${{ secrets.FTP_USER }}
        password: ${{ secrets.FTP_PASS }}
        server-dir: /home/sakodeko/public_html/
