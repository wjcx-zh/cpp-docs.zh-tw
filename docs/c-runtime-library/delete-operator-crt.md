---
title: "運算子 delete(CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "delete[]"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator delete[]"
  - "vector delete"
ms.assetid: e91bd0df-3815-40ca-950a-67b470518aed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算子 delete(CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

釋放已配置區塊。  
  
## 語法  
  
```  
  
      void __cdecl operator delete[](void * object);  
void __cdecl operator delete[](void * object,   
   void * memory) throw();  
void __cdecl operator delete[](void * object,   
   const std::nothrow_t&) throw();  
```  
  
#### 參數  
 *記憶體*  
 要釋放的記憶體位置。  
  
 *object*  
 要刪除之物件的指標。  
  
## 備註  
 這種形式的 **operator delete** 即為向量刪除，與純量刪除形式 \([operator delete](../c-runtime-library/operator-delete-crt.md)\) 形成對照。  
  
 **operator** `delete[]` 釋放 [operator new&#91;&#93;](../c-runtime-library/new-operator-crt.md) 配置的可用記憶體。  
  
 第一種形式的運算子稱為無放置 \(nonplacement\) 形式。  這個運算子的第二和第三種形式一般來說不會被從程式碼呼叫，而是當新放置失敗時，會存在讓編譯器有符合的刪除呼叫。  
  
 運算子的第一個形式是由編譯器定義的，而且不需要 new.h 包括在您的程式中。  
  
 加上了擲回的或無擲回例外的行為後， CRT **operator** `delete[]` 則與在 Standard C\+\+ 程式庫中的 [operator delete&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) 行為相同。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`delete[]`|\<new.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 使用運算子 **delete** 的範例，請參閱 [operator new&#91;&#93;](../c-runtime-library/new-operator-crt.md)。  
  
## 請參閱  
 [記憶體配置](../c-runtime-library/memory-allocation.md)