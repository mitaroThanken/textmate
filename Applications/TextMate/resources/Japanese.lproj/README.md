このフォルダ内のファイルについて
===

以下の手順で生成しています。

1. English.lproj のコピー 

	ベースとするEnglish.lprojをコピーします。

		cd Applications/TextMate/resources/
		cp -r English.lproj Japanese.lproj

2. English.strings ファイルの生成

	xibの変更点検出用の strings ファイルを生成します。
	ibtool を使用します。

		ibtool --generate-strings-file Japanese.lproj/MainMenu.English.strings English.lproj/MainMenu.xib
		ibtool --generate-strings-file Japanese.lproj/CreditsWindow.English.strings English.lproj/CreditsWindow.xib 

3. strings ファイルの生成

	修正する strings ファイルを生成します。
	ibtool を使用します。

		ibtool --generate-strings-file Japanese.lproj/MainMenu.strings English.lproj/MainMenu.xib
		ibtool --generate-strings-file Japanese.lproj/CreditsWindow.strings English.lproj/CreditsWindow.xib 

4. strings ファイルの修正

	生成された strings ファイルを修正します。
	
5. xibファイルの生成

	修正した strings ファイルを反映した、xib ファイルを生成します。ibtoolを使用します。

		ibtool -d Japanese.lproj/MainMenu.strings English.lproj/MainMenu.xib -W Japanese.lproj/MainMenu.xib
		ibtool -d Japanese.lproj/CreditsWindow.strings English.lproj/CreditsWindow.xib -W Japanese.lproj/CreditsWindow.xib

他のxibファイルも同様に修正可能と思われます。