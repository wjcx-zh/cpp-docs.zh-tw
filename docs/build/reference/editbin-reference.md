---
title: "EDITBIN 參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "editbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "二進位資料, 編輯"
  - "COFF 檔案, 編輯"
  - "EDITBIN 程式"
  - "目的檔, 修改"
ms.assetid: efdda03b-3dfc-4d31-90e6-caf5b3977914
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# EDITBIN 參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft COFF 二進位檔案編輯器 \(EDITBIN.EXE\) 可修改通用物件檔案格式 \(Common Object File Format，COFF\) 的二進位檔案 \(Binary File\)。  您可使用 EDITBIN 來修改目的檔 \(Object File\)、可執行檔和動態連結程式庫 \(DLL\)。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動這個工具。  您不能從系統命令提示字元或從檔案總管來啟動它。  
  
 在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上，無法使用 EDITBIN。  針對以 \/GL 所產生之二進位檔案的任何修改，都必須以重新編譯和連結來達成。  
  
-   [EDITBIN 命令列](../../build/reference/editbin-command-line.md)  
  
-   [EDITBIN 選項](../../build/reference/editbin-options.md)  
  
## 請參閱  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)