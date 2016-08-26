# Instalacao base
```
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
$ cd ~/.rbenv && src/configure && make -C src
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
$ source ~/.bash_profile
$ rbenv install 2.3.1
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
$ cd blog/_posts
$ vim ano-mes-dia-titulo.md # Siga o formato de um post já existente!
$ cd .. && jekyll build
$ git add _posts
$ git commit -m 'comentario a respeito do post'
$ git push origin -u master
```


# Links uteis
* http://daringfireball.net/projects/markdown/syntax
* https://jekyllrb.com/docs/usage
* https://www.git-tower.com/blog/git-cheat-sheet
