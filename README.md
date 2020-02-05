# PSSigntools
コードサイニング証明書を利用してexe/dllに署名するためのPowerShellスクリプト類

## sign.bat / sign.ps1
### 書式
` sign <ファイル1> [<ファイル2> ...]`
### 概要
引数で指定したファイルにコードサイニング証明書を使って署名する。署名できるファイルは  
* 実行形式ファイル(.exe .dll)
* PowerShellスクリプト(.ps1)

がある。
指定したファイルに有効な署名がない場合のみ署名するため、
既に有効な署名があるファイルに対しては何もしない。

sign.bat は sign.ps1 を呼び出すバッチファイル。  

## updatevsto.bat / updatevsto.ps1
### 書式
`  updatevsto.bat <ファイル.vsto>`
### 概要
OfficeアドインのDLLに署名し、関連するマニフェストファイルおよびVSTOインストーラーを再署名する。  

updatevsto.bat は updatevsto.ps1 を呼び出すバッチファイル。  

### sign / upadtevsto 使用時の注意点
コンピュータ上に有効なコードサイニング証明書が一つだけ登録されているという前提で
コードサイニング証明書を探索して使用するため、
複数のコードサイニング証明書を登録している環境での使用には適しません。

証明書の更新時期には古い証明書をアンインストールするなどの対応が必要になります。

タイムスタンプサーバーはGlobalSign http://timestamp.globalsign.com/scripts/timstamp.dll を
スクリプト内に埋め込んでいるため、変更したい場合はスクリプトを直接書き換える必要があります。
