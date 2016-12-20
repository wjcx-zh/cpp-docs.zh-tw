---
title: "BSCMAKE 命令列 | Microsoft Docs"
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
  - "BSCMAKE, 命令列"
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 命令列
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要執行 BSCMAKE，請使用下列命令列語法：  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 選項只能出現在命令列上的 `options` 欄位中。  
  
 *sbrfiles* 欄位指定編譯器或組合語言所建立的一或多個 .sbr 檔。  請以空格或 Tab 字元分隔 .sbr 檔的名稱。  您必須指定副檔名 \(沒有預設的副檔名\)。  您可以和檔名一起指定路徑，也可以使用作業系統萬用字元 \(\* 和 ?\)。  
  
 累加建置期間，您可以指定原本組建之中所沒有的新 .sbr 檔。  如果您希望將所有成果保留在瀏覽資訊檔中，必須指定原來建立 .bsc 檔時使用的所有 .sbr 檔 \(包含被截斷的檔案\)。  如果您省略了某個 .sbr 檔，該檔案對瀏覽資訊檔的成果就會被移除。  
  
 執行完整建置時，請不要指定被截斷的 .sbr 檔。  完整建置需要所有指定之 .sbr 檔的成果。  在您執行完整建置前，請重新編譯專案，並為每個空的檔案建立新的 .sbr 檔。  
  
 下列命令執行 BSCMAKE，以從三個 .sbr 檔建置一個名為 MAIN.bsc 的檔案：  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 如需相關資訊，請參閱 [BSCMAKE 命令檔](../../build/reference/bscmake-command-file-response-file.md)和 [BSCMAKE 選項](../../build/reference/bscmake-options.md)。  
  
## 請參閱  
 [BSCMAKE 參考](../../build/reference/bscmake-reference.md)