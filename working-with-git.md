# Práce s gitem

## Založení nové větve

Novou větev zakládáme vždy ze základní větve origin/staging.
Nová větev musí popisovat, co se v ní řeší, malými písmeny a slova oddělena pomlčkou (např: introducing-php-codesniffer)

~~~
git checkout -b new_branch_name origin/staging
~~~

Pokud práce ve větvi trvá délší dobu, ráno po příchodu do práce je dobré namergovat změny ve větvi origin/staging. předejde se tak případnému konfliktu.

~~~
git merge origin/staging
~~~

Jednotlivé komity by mely být atomické, do stage přidávat jen soubory, které se opravdu změnily. Zjistit stav stage jde příkazem gitu status.

~~~
git status                           # show stage status

git add path/changed_file_1          # adding files to commit stage
git add path/changed_file_2
git commit -m "Fixed a lot of typos" # commit 
~~~

Pozor: nezaměňovat git termín stage a větev origin/stage.
