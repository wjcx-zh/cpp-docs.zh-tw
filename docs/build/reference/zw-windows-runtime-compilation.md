---
title: "/ZW (Windows 執行階段編譯) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.CompileAsWinRT"
  - "/zw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ZW"
  - "/ZW 編譯器選項"
  - "Windows 執行階段編譯器選項"
  - "-ZW"
  - "-ZW 編譯器選項"
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /ZW (Windows 執行階段編譯)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編輯原始程式碼，以支援 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\) 建立 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  
  
 當您使用 **\/ZW** 編譯時，請一律同時指定 **\/EHsc**。  
  
## 語法  
  
```cpp  
/ZW /EHsc /ZW:nostdlib /EHsc  
```  
  
## 引數  
 nostdlib  
 表示 Platform.winmd、Windows.Foundation.winmd 和其他預設 Windows 中繼資料 \(.winmd\) 檔案未自動包含在編譯中。  相反地，您必須使用 [\/FU \(強制名稱的 \#using 檔案\)](../../build/reference/fu-name-forced-hash-using-file.md) 編譯器選項，明確指定 Windows 中繼資料檔案。  
  
## 備註  
 當您指定 **\/ZW** 選項時，編譯器支援下列功能：  
  
-   必要的中繼資料檔案、命名空間、資料類型和函式，您的應用程式需要它們以在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 執行。  
  
-   [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 物件的自動參考計數，以及在參考計數歸零時自動捨棄物件。  
  
 由於 Incremental Linker 不支援使用 **\/ZW** 選項包含在 .obj 檔案中的 Windows 中繼資料，[\/Gm \(啟用最少重建\)](../../build/reference/gm-enable-minimal-rebuild.md) 選項與 **\/ZW** 不相容。  
  
 如需詳細資訊，請參閱[Visual C\+\+ 語言參考](../Topic/Visual%20C++%20Language%20Reference%20\(C++-CX\).md)。  
  
## 需求  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)