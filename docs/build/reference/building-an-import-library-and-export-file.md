---
title: "建置匯入程式庫和匯出檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.ModuleDefinitionFile"
  - "VC.Project.VCLibrarianTool.ExportNamedFunctions"
  - "VC.Project.VCLibrarianTool.GenerateDebug"
  - "VC.Project.VCLibrarianTool.ForceSymbolReferences"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".lib 檔案"
  - "/DEF 程式庫管理員選項"
  - "/EXPORT 程式庫管理員選項"
  - "/INCLUDE 程式庫管理員選項"
  - "/OUT 程式庫管理員選項"
  - "DEF 程式庫管理員選項"
  - "-DEF 程式庫管理員選項"
  - "EXP 檔案"
  - "EXPORT 程式庫管理員選項"
  - "-EXPORT 程式庫管理員選項"
  - "匯出資料"
  - "匯出資料, 匯出 (.exp) 檔案"
  - "匯入程式庫, 建置"
  - "INCLUDE 程式庫管理員選項"
  - "-INCLUDE 程式庫管理員選項"
  - "OUT 程式庫管理員選項"
  - "-OUT 程式庫管理員選項"
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置匯入程式庫和匯出檔案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要建置匯入程式庫和匯出檔案，請使用下列語法：  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 當指定了 \/DEF，LIB 會根據傳遞至 LIB 命令內的匯出規格來建立輸出檔案。  有三種方法可指定匯出，依建議使用順序列出：  
  
1.  其中一個 *objfiles* 或 *libraries* 之內的 **\_\_declspec\(dllexport\)** 定義  
  
2.  在 LIB 命令列上 \/EXPORT:*name* 的規格  
  
3.  在 `deffile` 中的 **EXPORTS** 陳述式之內的定義  
  
 這些和您在連結匯出程式時指定匯出的方法相同。  一個程式中可以使用一種以上的方法。  您可以在 LIB 命令的命令檔裡指定部分的 LIB 命令 \(例如，多個 *objfiles* 或 \/EXPORT 規格\)，就如在 LINK 命令裡一樣。  
  
 下列選項可套用於建置匯入程式庫和匯出檔案：  
  
 \/OUT: *import*  
 覆寫正在建立之 *import* 程式庫的預設輸出檔案名稱。  當沒有指定 \/OUT 時，預設名稱是在 LIB 命令中之第一個目的檔或程式庫的主檔名，副檔名為 .lib。  匯出檔被指定為與匯入程式庫相同的主檔名，以及副檔名 .exp。  
  
 \/EXPORT: *entryname*\[\= *internalname*\]\[,@ `ordinal`\[, **NONAME**\]\]\[, **DATA**\]  
 從您的程式中匯出一個函式，以允許其他程式呼叫這個函式。  您也可以匯出資料 \(使用 **DATA** 關鍵字\)。  匯出通常定義於 DLL 中。  
  
 當呼叫的程式使用 *entryname* 時，它是函式或資料項目的名稱。  您也可以指定 *internalname* 做為定義程式中已知的函式；*internalname* 是預設為與 *entryname* 相同。  `ordinal` 指定索引到匯出表範圍 1 至 65,535 之間；如果您沒有指定 `ordinal`，LIB 會指派一個。  **NONAME** 關鍵字只以序數匯出函式，沒有 *entryname*。  **DATA** 關鍵字用來匯出只有資料的物件。  
  
 \/INCLUDE: `symbol`  
 將指定的符號加入符號表。  這個選項在強迫使用不會被包含的程式庫物件時很有用。  
  
 請注意，如果您在建立 .dll 之前的預備步驟中，建立匯入程式庫，則在建置 .dll 時，必須傳遞於建置匯入程式庫時所用的同一組物件檔。  
  
## 請參閱  
 [與匯入程式庫和匯出檔案一起使用](../../build/reference/working-with-import-libraries-and-export-files.md)