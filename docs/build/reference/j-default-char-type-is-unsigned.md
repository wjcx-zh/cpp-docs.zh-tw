---
title: "/J (預設 char 類型為 unsigned) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned"
  - "VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned"
  - "/j"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/J 編譯器選項 [C++]"
  - "char 資料類型"
  - "預設 char 類型為不帶正負號的"
  - "預設, char 類型"
  - "J 編譯器選項 [C++]"
  - "-J 編譯器選項 [C++]"
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# /J (預設 char 類型為 unsigned)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將預設 `char` 型別從 `signed char` 變更為 `unsigned char`，而且這個 `char` 型別在擴展為 `int` 型別時，是以零擴充的。  
  
## 語法  
  
```  
/J  
```  
  
## 備註  
 如果明確地將 `char` 值宣告為`signed`類型時，**\/J** 選項不會生效，且該值在擴展為 `int` 類型時，會以帶正負號的形式進行擴充。  
  
 **\/J** 選項定義了 `_CHAR_UNSIGNED`，它是用來配合 LIMITS.h 檔案中的 `#ifndef`，以定義預設 `char` 型別的範圍。  
  
 ANSI C 和 C\+\+ 並不要求 `char` 型別的特定實作。  如果您要使用最後會轉譯為英語以外語言的字元資料，這個選項就很有用處。  
  
> [!NOTE]
>  如果您使用 ATL\/MFC 的這個編譯器選項，可能會產生錯誤。  雖然您可以透過定義 `_ATL_ALLOW_CHAR_UNSIGNED`停用這個錯誤，這個作業卻不支援而且未必可行。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  在專案 \[**屬性頁**\] 對話方塊中，於 \[**組態屬性**\] 下左邊窗格中，展開 \[**C\/C\+\+**\]，然後選擇 \[**命令列**\]。  
  
3.  在 \[**其他選項**\] 窗格中，指定 **\/J** 編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)