# Deploying 

Jak deployovat : 

Napřed nahrajeme nové zdrojové kódy na cílový stroj. Protože zatím nemáme nic chytřejšího k dispozici, používáme 
[rsync](https://linux.die.net/man/1/rsync),
který nahraje změněné soubory z příslušných adresářů. Ty jsou uvedeny v souboru _rsync_include.txt_.

~~~bash
# na svem lokalnim stroji, kde bydli aplikace Tesco Clubcard, takze neco jako $ROOT/home/admin
cd TADY_JE_HOME_APLIKACE
rsync  -vv -r --exclude="app/config/config.local.neon" --files-from=./rsync_include.txt . ad-test:home/admin/

# pokud byly zmeny i v css a pod.
rsync -vv -r www/admin/ ad-test:www/admin
~~~

Nahrajeme nové php knihovny:

~~~bash
ssh ad-test                             # ssh login na prislusny stroj
php71 /usr/local/bin/composer install   # aktualni composer je nastaven na php56, proto explicitne php71
~~~

Nyní provedeme databázové migrace:

~~~bash
ssh ad-test                      # ssh login na prislusny stroj
cd home/admin                    # domovsky adresar aplikace 
source ~/home/.bashrc            # nahrani hesel a cest k pripojeni k databazi do shellu 
php71 vendor/bin/phinx status    # dobrovolne - kontrola, zda je nejaka migrace dostupna
php71 vendor/bin/phinx migrate   # vlastni provedeni migrace
~~~

Občas je dobré smazat cache a proxy databází na cílovem stroji, ale pozor na přihlášené uživatele:

~~~bash
ssh ad-test                    # ssh login na prislusny stroj
cd home/admin                  # domovsky adresar aplikace 
php71 vendor/bin/phing clean   # target smaze obsah adresaru cache a proxies
~~~

poznámka: ad-test - je alias (muj :), použijte plnou adresu s uživatelem nebo si ji nastavte v .ssh/config
