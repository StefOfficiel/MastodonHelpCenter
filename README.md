# MastodonHelpCenter
Page HelpCenter (Centre d'aide) pour votre instance Mastodon.

## Avant toute chose, pensez à faire un backup !

## Pour ajouter votre page custom :
Utilisez nano en SSH ou téléchargez et éditez le fichier :
`/home/mastodon/live/app/javascript/mastodon/features/ui/components/navigation_panel.jsx`

En dessous de `<ColumnLink transparent to='/lists'` et au dessus de `<ListPanel />` j'ai ajouté ceci :

```
<div className='helpcenter_menu'>
	<a className='column-link column-link--transparent' title="Centre d'aide" href="/helpcenter/index.html" style={{
		color: '#8c8dff',
	}}>
		<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 14 14"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"><path d="M6.998.552a6.448 6.448 0 0 0-5.367 10.02L.55 13.447l3.62-.655A6.448 6.448 0 1 0 6.999.552Z"></path><path d="M5.51 5.512A1.488 1.488 0 1 1 6.998 7v.992M7 10.472a.248.248 0 0 1 0-.496m0 .496a.248.248 0 1 0 0-.496"></path></g></svg><span>Centre d'aide</span>
	</a>
</div>
```

Vous pouvez customisez comme bon vous semble.

Sauvegardez ou ré-uploadez le fichier `navigation_panel.jsx`.

Puis connectez-vous en SSH et faites :

`service mastodon-web stop && service mastodon-sidekiq stop && service mastodon-streaming stop`

`su - mastodon`

`cd live`

`RAILS_ENV=production bundle exec rails assets:precompile`

`exit`

`service mastodon-web restart && service mastodon-sidekiq restart && service mastodon-streaming restart`

Vous devriez voir le nouveau bouton.

Note : Je n'ai pas trouver où se trouvait le menu pour le mode avancé.