---
title: "pgosweep | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pgosweep 程式"
  - "特性指引最佳化, pgosweep"
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# pgosweep
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用於特性指引最佳化，以將執行中程式的所有分析資料寫入 .pgc 檔案。  
  
## 語法  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### 參數  
 `options`  
 選擇性參數，可以留白。  `options` 的有效值如下：  
  
-   **\/?** 或 **\/help,**  會顯示說明訊息。  
  
-   **\/noreset,** 會保留執行階段資料結構中的計數。  
  
 `image`  
 使用編譯器選項 \/LTCG:PGINSTRUMENT 建立的 .exe 或 .dll 檔案的完整路徑。  
  
 `pgcfile`  
 這個命令會寫出資料計數的 .pgc 檔案。  
  
## 備註  
 這個命令適用於使用 \/LTCG:PGINSTRUMENT 編譯器選項建置的程式。  它會中斷執行中的程式，並將分析資料寫入新的 .pgc 檔案。  根據預設，這個命令會在每次寫入作業後重設計數。  如果有指定 **\/noreset** 選項，命令將會記錄值，但不會重設執行程式中的計數值。  如果於稍後擷取分析資料，這個選項會給您重複的資料。  
  
 `pgosweep` 的其他用法是只擷取應用程式執行階段的分析資訊。  舉例來說，您可以在啟動應用程式後馬上執行 `pgosweep`，並捨棄該檔案。  這樣可以移除與啟動成本關聯的分析資料。  接著，您可以在應用程式結束前執行 `pgosweep`。  現在，收集到的資料只會有執行階段的分析資訊。  
  
 當您命名 .pgc 檔 \(`pgcfile`\) 時，可以使用標準格式，也就是 *appname\!n*.pgc。  如果使用這種格式，編譯器會在 \/LTCG:PGO 階段中找到這項資料。  如果不使用標準格式，則必須使用 [pgomgr](../../build/reference/pgomgr.md)，以合併 .pgc 檔。  
  
## 範例  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 在這個範例中，`pgosweep` 會將 myapp.exe 目前的分析資訊寫入 myapp\!1.pgc。  
  
## 請參閱  
 [特性指引最佳化工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)