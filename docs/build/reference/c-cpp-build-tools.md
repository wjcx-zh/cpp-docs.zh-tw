---
title: "C/C++ 建置工具 | Microsoft Docs"
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
  - "c.build"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "組建 [C++], C/C++ tools"
  - "工具 [C++], 組建"
ms.assetid: 48d9daf4-6bbf-473a-8ce2-bf2923b69f80
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C/C++ 建置工具
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供下列用於檢視或操作建置 \(Build\) 輸出的命令列工具：  
  
-   [BSCMAKE.EXE](../../build/reference/bscmake-reference.md) 建置瀏覽資訊檔 \(.bsc\)，其中包含程式的符號 \(類別、函式、資料、巨集和型別\) 之詳細資訊。  您可在開發環境內的瀏覽視窗中檢視這項資訊 \(也可在開發環境中建置 .bsc 檔\)。  
  
-   [LIB.EXE](../../build/reference/lib-reference.md) 可用來建立及管理通用物件檔案格式 \(Common Object File Format，COFF\) 的物件檔案程式庫。  它也能夠用來建立匯出檔案和匯入程式庫來參考匯出定義。  
  
-   [EDITBIN.EXE](../../build/reference/editbin-reference.md) 可用來修改 COFF 二進位檔案 \(Binary File\)。  
  
-   [DUMPBIN.EXE](../../build/reference/dumpbin-reference.md) 顯示 COFF 二進位檔案的詳細資訊 \(例如符號表\)。  
  
-   [NMAKE](../../build/nmake-reference.md) 可讀取及執行 Makefile。  
  
-   錯誤查詢公用程式 [ERRLOOK](../../build/reference/value-edit-control.md) 會根據輸入的數值，擷取系統錯誤訊息或模組錯誤訊息。  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [裝飾名稱](../../build/reference/decorated-names.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [連結器選項](../../build/reference/linker-options.md)