git clone https://github.com/noahsantosdacruz-source/nom-du-projet.git
cd BTS-n-1-2026
npm install
npm start
git add .
git commit -m "Déploiement initial"
git push origin main
https://index.html.github.io/nom-du-projet/
name: Deploy to GitHub Pages
on:
  push:
    branches: ["main"]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Build (si nécessaire)
        run: |
          npm install
          npm run build

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
