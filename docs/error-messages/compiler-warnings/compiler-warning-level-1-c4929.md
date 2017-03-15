---
title: "編譯器警告 (層級 1) C4929 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4929"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4929"
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# 編譯器警告 (層級 1) C4929
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'file' : 型別程式庫包含一個等位；會忽略 'embedded\_idl' 限定詞  
  
 這個 [\#import](../../preprocessor/hash-import-directive-cpp.md) 的 embedded\_idl 屬性無法套用到此型別程式庫中，因為等位出現在型別程式庫中。  若要解決這個警告，請勿使用 embedded\_idl。  
  
## 範例  
 下列範例會定義元件。  
  
```  
// C4929a.cpp  
// compile with: /LD /link /TLBOUT:C4929a.tlb  
#include <objbase.h>  
[module(name="Test")];  
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {  
   [case(24)]  
      float fM;  
   [case(25)]  
      double dMN;  
   [default]  
      int x;  
} TD_UNION_TYPE;  
  
[export, public] typedef struct _TDW_TYPE {  
   [switch_is(sU)] TD_UNION_TYPE w;  
      short sU;  
} TD_TYPE;  
  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface I {  
   HRESULT f(TD_TYPE*);  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct C : I {  
   HRESULT f(TD_TYPE*) { return 0; }  
};  
```  
  
## 範例  
 下列範例會產生 C4929。  
  
```  
// C4929b.cpp  
// compile with: /c /W1  
#import "C4929a.tlb" embedded_idl   // C4929  
```