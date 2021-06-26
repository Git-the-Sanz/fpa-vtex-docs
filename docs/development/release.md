[Instrucciones](https://developers.vtex.com/vtex-developer-docs/docs/vtex-io-documentation-releasing-a-new-app-version){: .md-button .md-button--primary }

## Minors o Patches

1. Procurar tener mergeado los ultimos cambios con `git pull --rebase origin [BRANCH]`
2. `vtex release patch stable` esto va a generar un nuevo tag en el repo y comittear cambios del manifest y changelog
3. Si el release no lo hizo automaticamente, tendremos que hacer `vtex publish`
4. `vtex deploy --force`
5. Para finalizar, estando en el workspace donde tenemos la app instalada `vtex update`

---

## Majors o Breaking changes

1. Crear un nuevo workspace de produccion `vtex use [NAME] --production`
2. `vtex release major stable` + los pasos de publish y deploy
3. `vtex install` esto automaticamente reemplaza la major version anterior
4. `vtex browse` ir a CMS -> Graphql IDE (Si no esta, instalar)
5. Buscar `vtex.pages@2.x`
6. Ejecutar la siguiente mutation

```json 
mutation{
  updateThemeIds(from:"{appvendor}.{appname}@{oldmajor}.x", 
  to:"{appvendor}.{appname}@{newmajor}.x")
}
```  
Por ultimo, `vtex promote` esto reemplaza master con el workspace actual