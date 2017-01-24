---
title: "C# 和 C++ 的 VSCT 範例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 檔案, 範例"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# C# 和 C++ 的 VSCT 範例
VSCT 已成為新的定義命令的方式。  有鑑於此，變更發生在 VSCT 範例 C\# 和 c \+ \+ 編譯的方式。  與外部檔案的 c \+ \+ 中，並在 C\# 與.vsct 檔案中的 \[符號\] 區段中，現在所定義的命令。  
  
## 定義命令  
  
### C \+ \+ 的外部檔案  
 在 c \+ \+ 範例中，VSCT 編譯器會包含外部的檔案，來定義內定義的命令所使用的常數。  加入這些檔案，並藉此定義的命令定義常數的方法是將`Extern`標記內的.vsct 檔案，並指定名稱的外部檔案參考，在`href`屬性。  這些檔案包括：  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 從 c \+ \+.vsct 檔案的下列程式碼片段會示範如何將這些檔案包含：  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### C\# 符號  
 C\# 範例，在.vsct 檔案的`Symbols`本身定義命令檔中的區段。  在 C\# 的.vsct 檔案中的符號的定義源自於項目識別碼所定義的命令表裡的方式。  以下是從指定的命令，以及與其相關的常數 C\#.vsct 檔案的程式碼片段：  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## 內嵌點陣圖  
  
### C\#  
 C \+ \+ 和 C\# cto 能夠二進位碼檔案中的點陣圖會儲存在外部磁碟上。  點陣圖的 id 會定義方法，以便定義必須提供點陣圖中的 GUID 屬性`resID`屬性包含點陣圖，然後按一下 \[數字用在按鈕定義的項目 id，該點陣圖區域 \(`usedList`屬性\)。  這項宣告中重要的層面是項目 id 必須是點陣圖區域內的點陣圖的實際索引 \(以 1 起始\)。  
  
 下列範例所示，點陣圖區域已包含其中包含只有一個項目。  這個項目的 ID 是 guidMenuAndCommandsCmdSet:bmpArrow，以定義的所以 bmpArrow 必須定義為 1。  這也是點陣圖的宣告。  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## 請參閱  
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../Topic/Visual%20Studio%20Command%20Table%20\(.Vsct\)%20Files.md)