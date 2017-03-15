---
title: "/Fm (命名對應檔) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/fm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fm 編譯器選項 [C++]"
  - "檔案 [C++], 建立對應"
  - "Fm 編譯器選項 [C++]"
  - "-Fm 編譯器選項 [C++]"
  - "對應檔 [C++], 建立連結器"
ms.assetid: 8154448a-93a7-4546-8e4c-5c44d0aff45d
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Fm (命名對應檔)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示連結器產生對應檔，其中包含依區段出現在相對應 .exe 檔案或 DLL 中之順序排列的區段清單。  
  
## 語法  
  
```  
/Fmpathname  
```  
  
## 備註  
 根據預設，這個對應檔會被賦予對應 C 或 C\+\+ 原始程式檔的主檔名，再加上一個 .MAP 副檔名。  
  
 指定 **\/Fm** 與已指定 [\/MAP \(產生對應檔\)](../../build/reference/map-generate-mapfile.md) 連結器選項的作用相同。  
  
 如果您指定 [\/c \(編譯而不連結\)](../../build/reference/c-compile-without-linking.md) 以隱藏連結，**\/Fm** 就不會有任何作用。  
  
 對應檔中的全域符號通常有一個或多個前置底線，因為編譯器會加一個前置底線到變數的名稱。  許多出現在對應檔中的全域符號是由編譯器和標準程式庫在內部使用的。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [指定路徑名稱](../../build/reference/specifying-the-pathname.md)