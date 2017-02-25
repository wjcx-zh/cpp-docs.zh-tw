---
title: "/GX (啟用例外狀況處理) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GX 編譯器選項 [C++]"
  - "cl.exe 編譯器, 例外狀況處理"
  - "啟用例外狀況處理編譯器選項 [C++]"
  - "例外狀況處理, 啟用"
  - "GX 編譯器選項 [C++]"
  - "-GX 編譯器選項 [C++]"
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /GX (啟用例外狀況處理)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 `extern` C 函式永遠不會擲回例外狀況的假設下，啟用同步例外處理。  
  
## 語法  
  
```  
/GX  
```  
  
## 備註  
 它就相當於 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)。  
  
 當您從開發環境之內進行編譯時，**\/GX** 是預設為啟用。  使用命令列工具時，**\/GX\-** 是預設為啟用。  
  
 如需詳細資訊，請參閱[C\+\+ 例外狀況處理](../../cpp/cpp-exception-handling.md)。  
  
 **\/GX** 已被取代。請改用 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
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