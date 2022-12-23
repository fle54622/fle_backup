# fle_backupの目的
自分でプログラムを書いているときに簡単にバックアップが取れる機能がほしいと思った．

# コマンド一覧
rake backup_templat #バックアップ機能を使えるディレクトリを作成する　(入力 ディレクトリ名 バックアップの数 )  
rake backup_update  #バックアップをとる (入力 ディレクトリまでのパス )
rake backup_use #バックアップを使う (入力 ディレクトリまでのパス 使用するバックアップの数字 )
rake backup_add #バックアップの数を増やす (入力 ディレクトリまでのパス 追加するバックアップの数 )
rake backup_remove #バックアップの数を減らす (入力 ディレクトリまでのパス 削除するバックアップの数 )

# 想定しているディレクトリ構造
```
hoge - main - 
     |
     - backup - backup_1
              |
              - backup_2
                   :
              - backup_n
```
main のディレクトリの中身をバックアップを取ったり，バックアップを適用する# fle_backup
