---
title: "LINK 輸入檔 | Microsoft Docs"
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
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令輸入至連結器檔案 [C++]"
  - "檔案 [C++], LINK"
  - "匯入程式庫 [C++], 連結器檔案"
  - "輸入檔 [C++], LINK"
  - "LINK 工具 [C++], 輸入檔"
  - "連結器 [C++], 輸入檔"
  - "模組定義檔"
  - "模組定義檔, 連結器檔案"
  - "資源 [C++], 連結器檔案"
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LINK 輸入檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您必須為連結器提供含有目的檔、匯入及標準程式庫、資源、模組定義和命令輸入的檔案。  LINK 不會根據副檔名猜測檔案的內容。  LINK 會檢查每個輸入檔以判斷它是什麼類型的檔案。  
  
 命令列上的目的檔是依其出現在命令列上的順序處理。  程式庫也是依在命令列中出現的順序進行搜尋，但有如下進一步說明：從程式庫叫入目的檔時未解析的符號會先在該程式庫中搜尋，接著在命令列和 [\/DEFAULTLIB \(指定預設程式庫\)](../../build/reference/defaultlib-specify-default-library.md) 指示詞的隨後程式庫中搜尋，然後在命令列開始的任何程式庫中搜尋。  
  
> [!NOTE]
>  LINK 已不再接受分號 \(或其他任何字元\) 做為回應檔及順序檔中註解的開頭。  只有在模組定義檔 \(.def\) 中會將分號辨識為註解的開頭。  
  
 LINK 會使用以下類型的輸入檔：  
  
-   [.obj 檔](../../build/reference/dot-obj-files-as-linker-input.md)  
  
-   [.netmodule 檔案](../../build/reference/netmodule-files-as-linker-input.md)  
  
-   [.lib 檔](../../build/reference/dot-lib-files-as-linker-input.md)  
  
-   [.exp 檔](../../build/reference/dot-exp-files-as-linker-input.md)  
  
-   [.def 檔](../../build/reference/dot-def-files-as-linker-input.md)  
  
-   [.pdb 檔](../../build/reference/dot-pdb-files-as-linker-input.md)  
  
-   [.res 檔](../../build/reference/dot-res-files-as-linker-input.md)  
  
-   [.exe 檔](../../build/reference/dot-exe-files-as-linker-input.md)  
  
-   [.txt 檔](../../build/reference/dot-txt-files-as-linker-input.md)  
  
-   [.ilk 檔](../../build/reference/dot-ilk-files-as-linker-input.md)  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)