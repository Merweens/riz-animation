# 🎬 Quiz Animation Française

Un quiz ludique pour tester ses connaissances sur l’animation française et capturer des leads via un formulaire email.

## 🚀 Déploiement Netlify

1. Crée un compte Netlify : https://www.netlify.com
2. Connecte ton GitHub et choisis ce repo.
3. Clique sur "New Site from Git" > Sélectionne ton dépôt `quiz-animation`.
4. Dans les paramètres :
   - **Build command** : *(laisser vide)*
   - **Publish directory** : `/` *(racine)*
5. Lance le déploiement 🎉

Netlify générera une URL du type :  
`https://quiz-animation.netlify.app`  
Tu peux modifier ce nom dans Domain Settings.

---

## 🧩 Ajouter un outil de capture d’emails

Le script utilise une fonction `submitEmail()` que tu peux connecter à :

### Mailchimp

1. Crée une audience dans ton compte Mailchimp.
2. Gère une clé API depuis `Account > Extras > API keys`.
3. Utilise leur [API v3](https://mailchimp.com/developer/marketing/api/list-members/add-member-to-list/) avec `fetch()` :

```javascript
fetch("https://<dc>.api.mailchimp.com/3.0/lists/<list_id>/members/", {
  method: "POST",
  headers: {
    "Authorization": "apikey YOUR_API_KEY",
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    email_address: email,
    status: "subscribed"
  })
})
