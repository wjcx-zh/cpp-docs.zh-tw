---
title: "BSCMAKE 參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".bsc 檔案, 建置"
  - "瀏覽資訊檔 (.bsc), 建置"
  - "瀏覽視窗"
  - "bsc 檔案, 建置"
  - "BSCMAKE"
  - "BSCMAKE, 參考"
  - "Microsoft Browse Information Maintenance Utility"
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# BSCMAKE 參考
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

> [!WARNING]
>  雖然 BSCMAKE 仍隨著 Visual Studio 安裝，IDE 已不再使用它。  從 Visual Studio 2008 起，瀏覽和符號資訊會自動儲存在方案資料夾的 SQL Server .sdf 檔案中。  
  
 Microsoft Browse Information Maintenance Utility \(BSCMAKE.EXE\) 會自編譯期間建立的 .sbr 檔案建置瀏覽資訊檔 \(.bsc\)。  您會在物件瀏覽器中檢視瀏覽資訊檔。  如需物件瀏覽器的詳細資訊，請參閱[在物件瀏覽器中瀏覽](http://msdn.microsoft.com/zh-tw/53eb91aa-08c6-4299-8e3c-a877ae8d0c55)。  
  
 建置您的程式時，可以為您的程式自動建立瀏覽資訊檔，使用 BSCMAKE 來建置檔案。  如果您在 Visual C\+\+ 開發環境中建立您的瀏覽資訊檔，則不需要知道如何執行 BSCMAKE。  不過，您可能想要閱讀本主題，了解可用的選項。  
  
 如果您在開發環境之外建置程式，您仍然可以在環境中建立您可以檢查的自訂 .bsc。  對編譯期間建立的 .sbr 檔案執行 BSCMAKE。  
  
> [!NOTE]
>  您只能從 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示字元啟動此工具。  您無法從系統命令提示字元，或從 \[檔案總管\] 啟動它。  
  
 本節包括下列主題：  
  
-   [建置瀏覽資訊檔：概觀](../../build/reference/building-browse-information-files-overview.md)  
  
-   [建置 .bsc 檔](../../build/reference/building-a-dot-bsc-file.md)  
  
-   [BSCMAKE 命令列](../../build/reference/bscmake-command-line.md)  
  
-   [BSCMAKE 命令檔](../../build/reference/bscmake-command-file-response-file.md)  
  
-   [BSCMAKE 選項](../../build/reference/bscmake-options.md)  
  
-   [BSCMAKE 結束代碼](../../build/reference/bscmake-exit-codes.md)  
  
## 請參閱  
 [C\/C\+\+ 建置工具](../../build/reference/c-cpp-build-tools.md)