# Elasticsearch a kibana - poznámky k instalaci

Rozhodně nevyčerpávající poznámky k instalaci a správě elasticsearch. Zatím předpokádané použití je fulltextové hledání 
pro češtinu.

## Elastic search

Stručně, jak to uvést do chodu.

### Instalace, aneb co všechno potřebuju k životu

Uvažujeme instalaci z předpřipravené binárky, do budoucna na to dám do kupy docker.
Stažení aktuální verze **elastic search** https://www.elastic.co/products. A když už tam jsme, stáhneme rovnou i
**kibanu**.

Základní instalace je jednoduchá, rozbalíme stažený tarball, a protože je vše jednoduché, spustíme vlastní server a 
následné to i vyzkoušíme.

~~~bash
# rozbaleni archivu
tar -xzf elasticsearch-5.6.4.tar.gz

# tady elastic bydli
cd elasticsearch-5.6.4

# spustime instanci
./bin/elasticsearch --daemonize
~~~

A je to, po chvíli chroupání se na adrese http://localhost:9200 objeví známé **You Know, for Search**.

### Instalace pluginů

Pro vhledávání v češtině potřebujeme několik pluginů.
  
  - [icu analysis](https://www.elastic.co/guide/en/elasticsearch/plugins/current/analysis-icu.html) - podpora unicode 

~~~sh
# tady elastic bydli
cd elasticsearch-5.6.4

# spustime instalaci pluginu
./bin/elasticsearch-plugin install analysis-icu
~~~

A je to.

