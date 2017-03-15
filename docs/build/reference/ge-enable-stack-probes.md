---
title: "/Ge (啟用堆疊探查) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ge 編譯器選項 [C++]"
  - "啟用堆疊探查"
  - "Ge 編譯器選項 [C++]"
  - "-Ge 編譯器選項 [C++]"
  - "堆疊檢查呼叫"
  - "堆疊探查"
  - "堆疊, 堆疊探查"
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /Ge (啟用堆疊探查)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

對每一個需要區域變數儲存區的函式呼叫啟動堆疊探查 \(Stack Probe\)。  
  
## 語法  
  
```  
/Ge  
```  
  
## 備註  
 如果您重寫堆疊探查的功能，這項機制會很有用處。  建議您使用 [\/Gh \(啟用 \_penter 攔截函式\)](../../build/reference/gh-enable-penter-hook-function.md)，而不要重寫堆疊探查。  
  
 [\/Gs \(控制堆疊檢查呼叫\)](../../build/reference/gs-control-stack-checking-calls.md) 有相同的效果。  
  
 **\/Ge** 已被取代；編譯器將產生堆疊檢查。  如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
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