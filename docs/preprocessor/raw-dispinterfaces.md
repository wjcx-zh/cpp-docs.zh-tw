---
title: "raw_dispinterfaces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "raw_dispinterfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_dispinterfaces 屬性"
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# raw_dispinterfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 告知編譯器為呼叫 **IDispatch::Invoke** 並傳回 `HRESULT` 錯誤碼的分配介面 \(Dispinterface\) 方法和屬性產生低階包裝函式。  
  
## 語法  
  
```  
raw_dispinterfaces  
```  
  
## 備註  
 如果沒有指定此屬性，只會產生高階包裝函式，一旦失敗就會擲回 C\+\+ 例外狀況。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)