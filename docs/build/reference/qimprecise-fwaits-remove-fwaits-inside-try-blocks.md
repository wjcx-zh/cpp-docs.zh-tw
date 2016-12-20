---
title: "/Qimprecise_fwaits (移除 Try 區域內的 fwaits) | Microsoft Docs"
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
  - "/Qimprecise_fwaits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Qimprecise_fwaits 編譯器選項 (C++)"
  - "-Qimprecise_fwaits 編譯器選項 (C++)"
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qimprecise_fwaits (移除 Try 區域內的 fwaits)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [\/fp:except](../../build/reference/fp-specify-floating-point-behavior.md) 編譯器選項時，移除 `try` 內部的 `fwait` 命令。  
  
## 語法  
  
```  
/Qimprecise_fwaits  
```  
  
## 備註  
 當沒有同時指定 **\/fp:except** 時，這個選項沒有作用。  如果指定 **\/fp:except** 選項，編譯器會在 `try` 區塊的每一個程式碼行前後加入 `fwait` 命令。  這樣，編譯器可以識別出產生例外狀況的特定程式碼行。  **\/Qimprecise\_fwaits** 會移除內部的 `fwait` 指令，只留下 `try` 區塊前後的等候。  這樣做會改善效能，但編譯器將只能指出哪個 `try` 區塊造成例外狀況，而非哪一行。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/Q 選項 \(低階運算\)](../../build/reference/q-options-low-level-operations.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)