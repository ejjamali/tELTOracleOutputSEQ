# tELTOracleOutputSEQ
Le composant tELTOracleOutputSEQ est une évolution, du composant tELTOracleOutput de Talend, qui permet l'utilisation d'une séquence dans le cas MERGE. 

# Installation
Voici les étapes à suivre pour installer le composant :
<ul>
<li>1. Spécifier un dossier pour les composants utilisateur 
    il faut se rendre dans le menu Windows -> Preferences -> Talend -> Components 
      dans le champ <b>Dossier des composants utilisateur</b> renseigner le dossier dans lequel vous allez déposer le nouveau composant. Par exemple : 
      <i>C:\Talend5.6.1\TOS_DI-20141207_1530-V5.6.1\custom</i>
<li>2. Télécharger le zip d'ici et le sauvegarder dans le dossier spécifier dans l'étape 1 </li>

<li>3. En fonction de votre version, modifier le fichier <b>tELTOracleOutputSEQ_main.javajet</b>. La ligne suivante doit pointer sur le bon répertoire du fichier <b>Log4jDBConnUtil.javajet </b>: 
    <%@ include file="../../plugins/org.talend.designer.components.localprovider_5.6.1.20141207_1530/components/templates/Log4j/Log4jDBConnUtil.javajet"%>
    </li>
</ul>     

Une fois l'installation, utilisez les touches CTRL+SHIFT+F3 afin de faire apparaitre le nouveau composant dans le palette. 

# Utilisation
Voici les étapes à suivre pour utiliser le composant:
<ul>
<li>1. Relier le nouveau composant à un tELTOracleMap</li>
<li>2. Paramétrer le composant en suivant la capture d'écran ci-dessous :
<img src="images/usage.png" alt="hi" class="inline"/>
</li>
<li>3. Spécifier la clé fonctionnelle de la table car celle-ci sera utilisée pour générer la rquête du MERGE. Cf. la capture d'écran ci-dessous. 
<img src="images/schema.png" alt="hi" class="inline"/>
</li>
</ul>


# Résultat 
Voici la requête générée et envoyée au SGBD :
MERGE INTO DIM_AUDIT target USING
  (SELECT NULL,
          SRC_AUDIT.NOM_SOURCE,
          SRC_AUDIT.STATUT,
          SYSTIMESTAMP AS INSERT_DATE,
          SYSTIMESTAMP AS UPDATE_DATE
   FROM SRC_AUDIT) SOURCE ON (target.NOM_SOURCE=source.NOM_SOURCE) WHEN MATCHED THEN
UPDATE
SET target.STATUT=source.STATUT,
    target.UPDATE_DATE=source.UPDATE_DATE WHEN NOT MATCHED THEN
INSERT (ID_AUDIT,
        NOM_SOURCE,
        STATUT,
        INSERT_DATE,
        UPDATE_DATE)
VALUES (SEQ_DIM_AUDIT.NEXTVAL,
        source.NOM_SOURCE,
        source.STATUT,
        source.INSERT_DATE,
        source.UPDATE_DATE)





