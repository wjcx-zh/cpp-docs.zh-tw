---
title: "LINK 環境變數 | Microsoft Docs"
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
  - "環境變數 [C++], LINK"
  - "LIB 環境變數"
  - "LINK 工具 [C++], 環境變數"
  - "變數, 環境"
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LINK 環境變數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LINK 工具使用下列環境變數：  
  
-   LINK 和 \_LINK\_ \(若已定義\)。  在處理命令列引數之前，LINK 工具會在前面加上 LINK 環境變數中定義的引數選項和引數，並在後面附加 \_LINK\_ 環境變數中定義的選項和引數。  
  
-   LIB \(若已定義\)。  LINK 工具在搜尋命令列上或以 [\/BASE](../../build/reference/base-base-address.md) 選項所指定的物件、程式庫或其他檔案時會使用 LIB 路徑。  它也會使用 LIB 路徑來尋找物件中指定的 .pdb 檔案。  LIB 變數可以包含一或多個以分號分隔的路徑規格。  一個路徑必須指向 Visual C\+\+ 安裝的 \\lib 子目錄。  
  
-   PATH，如果該工具必須執行 CVTRES，但在 LINK 本身的相同目錄中找不到檔案。  \(LINK 需要 CVTRES 才能連結 .res 檔案。\) PATH 必須指向 Visual C\+\+ 安裝的 \\bin 子目錄。  
  
-   TMP，在連結 OMF 或 .res 檔案時指定目錄。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [設定命令列建置的路徑和環境變數](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)