# 位相一貫性検証機能

## 概要

3D都市モデルの品質管理支援のための位相一貫性検証機能です。

本ソフトウェアは、国土交通省の[Project PLATEAU](https://www.mlit.go.jp/plateau/)で開発した[品質評価システム](https://github.com/Project-PLATEAU/CityGML-evaluation-system)で利用した、3D都市モデルの位相一貫性検証機能（FME Workspace）です。対応データ形式は[OGC CityGML 2.0](https://www.ogc.org/standards/citygml)形式です。また、CityGMLの拡張仕様であるADE（Application Domain Extension）にも対応しており、内閣府地方創生推進事務局が定めた[i-都市再生技術仕様案 v1.4 (iｰUR 1.4)](https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/)などにも対応可能です。


**ただし、i-UR1.4は2021年9月にi-UR1.5に改定されました。これに伴い、URLが変更されました。**

そのため、本ソフトウェアの利用にあたり、3D都市モデル（CityGML形式）及びソフトウェアに記述された旧URLを新しいURLに更新する必要があります。

具体的には以下の手順に従い、更新してください。

## 1．3D都市モデル（CityGML形式）に記述されたURLの更新

3D都市モデルのファイル内の名前空間とschemaLocationに記載されている旧URLを新しいURLに更新（テキスト置換）してください。

対象となる記述を下表に示します。

- 名前空間

|旧URL（i-UR1.4のURL）|新しいURL（i-UR1.5のURL）|
| - | - |
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/uro/1.4`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/uro/1.5|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/urf/1.4`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/urf/1.5|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/urg/1.4`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/urg/1.5|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/urt/1.4`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/urt/1.5|

- schemaLocation

|旧URL（i-UR1.4のURL）|新しいURL（i-UR1.5のURL）|
| - | - |
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.4/urbanObject.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.5/urbanObject.xsd|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/urf/1.4/urbanFunction.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.5/urbanFunction.xsd|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.4/statisticalGrid.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.5/statisticalGrid.xsd|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.4/publicTransit.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.5/publicTransit.xsd|

----
置換には、Visual Studio CodeやXMLEDITOR.NETなどのツールをご利用ください。  
名前空間及びschemaLocationは、3D都市モデル（CityGML形式）の、`<core:CityModel>`の開始タグに記載されています。  
置換前後の3D都市モデル（CityGML形式）の例を以下に示します。太字部分が置換対象となる箇所です。  
#### 置換前
<core:CityModel xmlns:uro="**`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/uro/1.4`**" xmlns:core="http://www.opengis.net/citygml/2.0"
xmlns:luse="http://www.opengis.net/citygml/landuse/2.0" xmlns:bldg="http://www.opengis.net/citygml/building/2.0"
xmlns:tran="http://www.opengis.net/citygml/transportation/2.0" xmlns:grp="http://www.opengis.net/citygml/cityobjectgroup/2.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:gml="http://www.opengis.net/gml" xmlns:xlink="http://www.w3.org/1999/xlink"
xsi:schemaLocation="**`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/uro/1.4
http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.4/urbanObject.xsd`** http://www.opengis.net/citygml/2.0
http://schemas.opengis.net/citygml/2.0/cityGMLBase.xsd http://www.opengis.net/citygml/landuse/2.0 http://schemas.opengis.net/citygml/landuse/2.0/landUse.xsd
http://www.opengis.net/citygml/building/2.0 http://schemas.opengis.net/citygml/building/2.0/building.xsd http://www.opengis.net/citygml/transportation/2.0
http://schemas.opengis.net/citygml/transportation/2.0/transportation.xsd http://www.opengis.net/citygml/cityobjectgroup/2.0
http://schemas.opengis.net/citygml/cityobjectgroup/2.0/cityObjectGroup.xsd http://www.opengis.net/gml http://schemas.opengis.net/gml/3.1.1/base/gml.xsd">
#### 置換後
<core:CityModel xmlns:uro="**`https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/uro/1.5`**" 
xmlns:core="http://www.opengis.net/citygml/2.0"
xmlns:luse="http://www.opengis.net/citygml/landuse/2.0" xmlns:bldg="http://www.opengis.net/citygml/building/2.0"
xmlns:tran="http://www.opengis.net/citygml/transportation/2.0" xmlns:grp="http://www.opengis.net/citygml/cityobjectgroup/2.0"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:gml="http://www.opengis.net/gml" xmlns:xlink="http://www.w3.org/1999/xlink"
xsi:schemaLocation="**`https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/uro/1.5 https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.5/urbanObject.xsd`**  
http://www.opengis.net/citygml/2.0 http://schemas.opengis.net/citygml/2.0/cityGMLBase.xsd http://www.opengis.net/citygml/landuse/2.0
http://schemas.opengis.net/citygml/landuse/2.0/landUse.xsd http://www.opengis.net/citygml/building/2.0 http://schemas.opengis.net/citygml/building/2.0/building.xsd
http://www.opengis.net/citygml/transportation/2.0 http://schemas.opengis.net/citygml/transportation/2.0/transportation.xsd http://www.opengis.net/citygml/cityobjectgroup/2.0
http://schemas.opengis.net/citygml/cityobjectgroup/2.0/cityObjectGroup.xsd http://www.opengis.net/gml http://schemas.opengis.net/gml/3.1.1/base/gml.xsd">

## 2．ソフトウェアに記述されたURL及びバージョンの更新

FME Workbenchspaceにおいて本スクリプトを実行する際、Transportation Parameter ValuesでAdditional ADE Schema File(s)をURLで指定している場合は、新しいschemaLocationのURLを指定する必要があります。

（指定していない場合は、更新の必要はありません）

- schemaLocation

|旧URL（i-UR1.4のURL）|新しいURL（i-UR1.5のURL）|
| - | - |
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.4/urbanObject.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.5/urbanObject.xsd|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/urf/1.4/urbanFunction.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/uro/1.5/urbanFunction.xsd|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.4/statisticalGrid.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.5/statisticalGrid.xsd|
|`http://www.kantei.go.jp/jp/singi/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.4/publicTransit.xsd`|https://www.chisou.go.jp/tiiki/toshisaisei/itoshisaisei/iur/schemas/urg/1.5/publicTransit.xsd|



また、本ソフトウェアの動作には前提ソフトウェア（商用ソフトウェア）が必要で、単独では利用できません。位相一貫性検証機能の実装例として参考にして下さい。

なお、本ソフトウェアはドイツ[virtualcitysystems社](https://vc.systems/en/)が開発した製品機能を、オープンソースとして公開するためご提供を頂いたものです。virtualcitysystems社に感謝します。

機能一覧

* runner.fmw：複数CityGMLをZIP圧縮したファイルを検証します。パラメータMAX_PROCの指定に応じてマルチプロセスで実行できます。
* CityGMLValidation.fmw：CityGMLファイルを検証します。パラメータで検証内容を指定し、また検証結果（JSON形式のログファイル）の出力先を設定できます。

## 動作環境、前提ソフトウェア

動作環境

* Windows (Windows Server 2016 Datacenterで動作確認)

前提ソフトウェア

* 商用ソフトウェア：[FME Desktop](https://www.safe.com/fme/fme-desktop/)

## 利用方法

1. 上記の前提ソフトウェアをインストールします。
1. 本レポジトリの一式をダウンロードし、任意のディレクトリに置きます。
1. FME WorkbenchでCityGMLValidation.fmwを開いて実行するか、またはコマンドラインからパラメータを指定してFME.exeを実行して下さい。

	fme.exe CityGMLValidation.fmw --INPUT "CityGML.gml" --ADE_XSD_DOC "" --SRS_AXIS "2\<comma\>1\<comma\>3" --COORD "EPSG:6677" --OVER_CHECK "LoD2" --OVERLAP "5" --TOLERANCE "0.001" --BOUNDEDBY "Yes" --PREC "3" --PLAN_ANG "20" --PLAN_DIST "0.03" --OUTPUT "report.json"
	
	fme.exe runner.fmw --INPUT "CityGML.zip" --ADE_XSD_DOC "" --SRS_AXIS "2\<comma\>1\<comma\>3" --COORD "EPSG:6677" --OVER_CHECK "LoD2" --OVERLAP "5" --TOLERANCE "0.001" --BOUNDEDBY "Yes" --PREC "3" --PLAN_ANG "20" --PLAN_DIST "0.03" --OUTPUT "OutputFolder" --MAX_PROC "7" --WORKSPACE_FILE "CityGMLValidation.fmw" --LOG "logs"

1. パラメータの詳細は[ドキュメント](doc/documentation.pdf)を参照して下さい。注意点は下記です
	1. COORD：緯経度から平面直角座標系に変換して検証するため、対象都市毎に適切な系のEPSGコードを指定。
	1. OVER_CHECK：重複判定を実施する対象。通常は"LoD2"だが計算リソースを要するため、必須でなければ"No"としても良い。
	1. TOLERANCE：0.001は「1mm以内の近接点をエラーと検出する」の意味。より詳細なモデルでは0.0001など適切に変更しても良い。
	1. PREC：計算誤差を考慮し、近接点を同一点にSnap処理する単位。3は「1mm」の意味だが、モデルの有効桁数に応じて8など詳細化しても良い。

1. ログファイルにエラーが出力された場合、[ログコード一覧](doc/log.pdf)を参照し、エラーの原因を分析して下さい。


## ライセンス

Copyright (C) 2021 virtualcitysystems, GmbH.

本ソフトウェアは[Apache-2.0 License](LICENSE)を適用します。

## 注意事項

* 本レポジトリは参考資料として提供しているものです。動作保証は行っておりません。
* 予告なく変更・削除する可能性があります。
* 本レポジトリの利用により生じた損失及び損害等について、国土交通省及び著作権者はいかなる責任も負わないものとします。

## 参考資料

* 品質評価システム: https://github.com/Project-PLATEAU/CityGML-evaluation-system
* モデル自動生成システム: https://github.com/Project-PLATEAU/CityGML-production-system
* 書式・概念一貫性検証機能: https://github.com/Project-PLATEAU/CityGML-validation-function
