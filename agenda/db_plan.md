# DB設計

## 作成者
* @ayamakias

## 案１
* Books 書籍マスタ
|主キー|列名|型|NULL許可|デフォルト|説明|備考|
|:--:|:--|:--|:--:|:--|:--|:--|
|◯|isbn|INT(13)||ISBNコード|"ISBNさえ持っておけば国会図書館APIで書籍情報とってこれる。画像がないので、amazonの方が良いかも"|
| |registerTime|DATETIME|◯||登録日| |
| |registerUser|SMALLINT(5)|◯|0|登録者| |
| |updateTime|DATETIME|◯|CURRENT TIMESTAMP|更新日| |
| |updateUser|SMALLINT(5)|◯|0|更新者| |
| |invalid|TINYINT(1)||0|無効判定| |

* BookRentalStatus　書籍貸出状況
|主キー|列名|型|NULL許可|デフォルト|説明|備考|
|:--:|:--|:--|:--:|:--|:--|:--|
|◯|id|INT(10)| |AUTO INCREMENT|ID| |
| |bookId|INT(10)| |0|書籍ID|	|
| |userId|SMALLINT(5)| |0|ユーザーID| |
| |status|TINYINT(2)| |0|貸出状況 1: 予約中 2: 貸出中 3: 返却済|	|
| |lentFrom|DATETIME|◯|NULL|貸出日|列名微妙。|
| |scheduledLentTo|DATETIME|◯|NULL|返却予定日| |
| |lentTo	DATETIME|◯|NULL|返却日| |

* Users　ユーザーマスタ
|主キー|列名|型|NULL許可|デフォルト|説明|備考|
|:--:|:--|:--|:--:|:--|:--|:--|
|◯|id|INT(10)| |AUTO INCREMENT|ユーザーID| |
| |lastName|VARCHER(255) | |姓| |
| |firstName|VARCHER(255) | |名| |
| |lastNameKana|VARCHER(255)|◯|NULL|姓カナ| |
| |firstNameKana|VARCHER(255)|◯|NULL|名カナ| |
| |email|VARCHER(255)|◯|NULL|メールアドレス| |
| |password|VARCHER(255)| | |パスワード|ハッシュ？|
| |registerTime|DATETIME|◯|NULL|登録日| |
| |registerUser|SMALLINT(5)|◯|0|登録者| |
| |updateTime|DATETIME|◯|CURRENT TIMESTAMP|更新日| |
| |updateUser|SMALLINT(5)|◯|0|更新者| |
| |invalid|TINYINT(1)| |0|無効判定| |
