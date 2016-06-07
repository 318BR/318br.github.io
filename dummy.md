# Instalacao base
```
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
$ cd ~/.rbenv && src/configure && make -C src
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
$ source ~/.bash_profile
$ rbenv install 1.9.3-p194
```
---
# Clonar blog
```
$ rbenv rehash
$ gem install bundle
$ git clone git@github.com:318br/318br.github.io blog
$ cd blog && bundle install
```
---
# Novo post
```
$ cd blog/_post
$ vim ano-mes-dia-titulo.md # Siga o formato de um post já existente
$ jekyll build
$ git add _posts
$ git commit -m 'comentario a respeito do post'
$ git push origin -u master
```

