*github提供了github Pages来搭建一个小型的blog，步骤如下：*
1. 创建github帐号
2. 创建一个新的repo，**该repo的名字，必须保持格式<username>.github.io**，其中<username>替换成你的github账户名，然后点击确定，完成仓库的创建
3. git clone到本地，push一个index.html到远程repo，可用markdown生成
   
        …or create a new repository on the command line

        echo "# SwimmerRcd.github.io" >> README.md
        git init
        git add README.md
        git commit -m "first commit"
        git remote add origin git@github.com:SwimmerRcd/SwimmerRcd.github.io.git
        git push -u origin master
                        

        …or push an existing repository from the command line

        git remote add origin git@github.com:SwimmerRcd/SwimmerRcd.github.io.git
        git push -u origin master

        …or import code from another repository

        You can initialize this repository with code from a Subversion, Mercurial, or TFS project.

4. 进入远程repos `<username>.github.io`，点击settings选项卡，向下拖动到GitHub Pages模块，可以看到 Your site is published at `https://<username>.github.io/`
5. 这时候打开博客网站`https://<username>.github.io`，你就可以看到你的博客了