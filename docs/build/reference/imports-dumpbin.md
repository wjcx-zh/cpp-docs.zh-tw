---
title: "/IMPORTS (DUMPBIN) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/imports"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/IMPORTS dumpbin 選項"
  - "IMPORTS dumpbin 選項"
  - "-IMPORTS dumpbin 選項"
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /IMPORTS (DUMPBIN)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/IMPORTS[:file]  
```  
  
 這個選項會顯示匯入至可執行檔或 DLL 中之 DLL \(包括靜態連結的和[延遲載入的](../../build/reference/linker-support-for-delay-loaded-dlls.md)\) 清單，以及來自這些 DLL 中的所有各個匯入。  
  
 選擇性 \(Optional\) 的 `file` 規格可讓您指定只顯示該 DLL 的匯入。  例如：  
  
```  
dumpbin /IMPORTS:msvcrt.dll  
```  
  
## 備註  
 這個選項所顯示的輸出與 [\/EXPORTS](../../build/reference/dash-exports.md) 輸出類似。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 選項可用在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)