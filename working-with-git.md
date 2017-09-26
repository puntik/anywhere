# Práce s gitem a proces vývoje

## Založení nové větve

Novou větev zakládáme vždy ze základní větve origin/staging.
Nová větev musí popisovat, co se v ní řeší, malými písmeny a slova oddělena pomlčkou (např: introducing-php-codesniffer).
Veškerá práce probíhá pod běžným uživatelem (platí pro linuxové a mac uživatele), takže žádné `su` nebo `sudo`.

~~~
git checkout -b new_branch_name origin/staging
~~~

## Denní práce s gitem

Pokud práce ve větvi trvá délší dobu, ráno po příchodu do práce je dobré namergovat změny ve větvi *origin/staging*. předejde se tak případnému konfliktu.

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

Po dokončení práce provést push, který vytvoří novou větev na origin. Před pushem je dobré provést kontrolu změněných kódů.

~~~
git diff origin/stage # show changes against parent branch origin/state
git push              # push changes to origin
~~~

## Založení merge requestu

TBD :)
