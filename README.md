# tELTOracleOutputSEQ
Le composant tELTOracleOutputSEQ est une évolution, du composant tELTOracleOutput de Talend, qui permet l'utilisation d'une séquence dans le cas MERGE. 

# Installation
Voici les étapes à suivre afin d'installer le composant :
1. Spécifier un dossier pour les composants utilisateur 
    il faut se rendre dans le menu Windows -> Preferences -> Talend -> Components 
      dans le champ <b>Dossier des composants utilisateur</b> renseigner le dossier dans lequel vous allez déposer le nouveau composant. Par exemple : 
      <i>C:\Talend5.6.1\TOS_DI-20141207_1530-V5.6.1\custom</i>
2. Télécharger le zip d'ici et le sauvegarder dans le dossier spécifier dans l'étape 1

3. En fonction de votre version, modifier le fichier <b>tELTOracleOutputSEQ_main.javajet</b>. La ligne suivante doit pointer sur le bon répertoire du fichier <b>Log4jDBConnUtil.javajet </b>: 
    <%@ include file="../../plugins/org.talend.designer.components.localprovider_5.6.1.20141207_1530/components/templates/Log4j/Log4jDBConnUtil.javajet"%>      

Une fois l'installation, utilisez les touches CTRL+SHIFT+F3 afin de faire apparaitre le nouveau composant dans le palette. 

# Utilisation

