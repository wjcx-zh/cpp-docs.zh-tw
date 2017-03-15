---
title: "/Zs (僅檢查語法) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zs 編譯器選項 [C++]"
  - "Syntax Check Only 編譯器選項"
  - "Zs 編譯器選項"
  - "-Zs 編譯器選項 [C++]"
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /Zs (僅檢查語法)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示編譯器只檢查命令列上原始程式檔的語法。  
  
## 語法  
  
```  
/Zs  
```  
  
## 備註  
 使用這個選項時，不會建立任何輸出檔案，而錯誤訊息是寫入標準輸出中。  
  
 **\/Zs** 選項提供了快速方法，可在編譯和連結原始程式檔之前尋找並更正語法錯誤。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)