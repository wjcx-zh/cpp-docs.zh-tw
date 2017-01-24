---
title: "/GH (啟用 _pexit 攔截函式) | Microsoft Docs"
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
  - "_pexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gh 編譯器選項 [C++]"
  - "_pexit 函式"
  - "Gh 編譯器選項 [C++]"
  - "-Gh 編譯器選項 [C++]"
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GH (啟用 _pexit 攔截函式)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在每一個方法或函式結束時呼叫 `_pexit`  函式。  
  
## 語法  
  
```  
/GH  
```  
  
## 備註  
 `_pexit`  函式並非任何程式庫的一部分，必須由您提供 `_pexit` 的定義。  
  
 除非您打算明確地呼叫 `_pexit`，否則您不需要提供原型。  這個函式必須如同擁有下列原型一樣地出現，而且它必須在進入時推入所有暫存器的內容並且在離開時取出未變更的內容：  
  
```  
void __declspec(naked) _cdecl _pexit( void );  
```  
  
 `_pexit` 很類似 `_penter`；如需有關如何撰寫 `_pexit` 函式的範例，請參閱 [\/Gh \(啟用 \_penter 攔截函式\)](../../build/reference/gh-enable-penter-hook-function.md)。  
  
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