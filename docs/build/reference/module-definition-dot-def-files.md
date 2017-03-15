---
title: "模組定義檔案 (.Def) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".def 檔案"
  - "def 檔案"
  - "模組定義檔"
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 模組定義檔案 (.Def)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

模組定義檔案 \(Module\-Definition File，.def\) 提供連結器 \(Linker\) 有關於匯出、屬性 \(Attribute\) 的資訊，以及其他有關要連結之程式的資訊。  .def 檔案在建置 DLL 時最為有用。  由於可使用[連結器選項](../../build/reference/linker-options.md)取代模組定義陳述式，所以通常不需要 .def 檔。  您也可以使用 [\_\_declspec\(dllexport\)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) 做為指定匯出函式的一種方法。  
  
 您可以在連結器階段使用 [\/DEF \(指定模組定義檔案\)](../../build/reference/def-specify-module-definition-file.md) 連結器選項叫用 .def 檔。  
  
 如果您正建置一個沒有匯出的 .exe 檔，那麼使用 .def 檔會讓輸出檔案變大而且載入更慢。  
  
 如需範例，請參閱 [使用 DEF 檔案從 DLL 匯出](../../build/exporting-from-a-dll-using-def-files.md)。  
  
 如需詳細資訊，請參閱下列章節：  
  
-   [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)  
  
-   [EXPORTS](../../build/reference/exports.md)  
  
-   [HEAPSIZE](../../build/reference/heapsize.md)  
  
-   [LIBRARY](../../build/reference/library.md)  
  
-   [NAME](../../build/reference/name-c-cpp.md)  
  
-   [SECTIONS](../../build/reference/sections-c-cpp.md)  
  
-   [STACKSIZE](../../build/reference/stacksize.md)  
  
-   [STUB](../../build/reference/stub.md)  
  
-   [VERSION](../../build/reference/version-c-cpp.md)  
  
-   [保留字](../../build/reference/reserved-words.md)  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [Frequently Asked Questions on Building](http://msdn.microsoft.com/zh-tw/56a3bb8f-0181-4989-bab4-a07ba950ab08)