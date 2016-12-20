---
title: "embedded_idl | Microsoft Docs"
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
  - "embedded_idl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "embedded_idl 屬性"
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# embedded_idl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 指定類型程式庫將寫入 .tlh 檔，並保留屬性產生的程式碼。  
  
## 語法  
  
```  
embedded_idl[("param")]  
```  
  
#### 參數  
 `param`  
 可以是下列兩個值之一：  
  
-   emitidl: 從 typelib 匯入的類型資訊會出現在針對屬性化專案產生的 IDL 中。這是預設值，如果未指定 `embedded_idl` 的參數就會生效。  
  
-   no\_emitidl: 從 typelib 匯入的類型資訊不會出現在針對屬性化專案產生的 IDL 中。  
  
## 範例  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## 備註  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)