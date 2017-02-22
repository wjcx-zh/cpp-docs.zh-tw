---
title: "編譯器警告 (層級 1) C4312 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4312"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4312"
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 1) C4312
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operation' : 將 'type1' 轉換為較大的 'type2'  
  
 這項警告偵測到嘗試將 32 位元值指派給 64 位元指標類型的動作，例如，將 32 位元 `int` 或 `long` 轉型為 64 位元指標。  
  
 這可能是不安全的轉換，即使在發生正負號擴充時納入 32 位元指標值也是如此。  負的 32 位元整數指派給 64 位元指標類型，正負號擴充會使指標值參考不同於整數值的記憶體位址。  
  
 只會針對 64 位元編譯目標發出這個警告。  如需詳細資訊，請參閱[使用指標的規則](http://msdn.microsoft.com/library/windows/desktop/aa384242)。  
  
 為 64 位元目標編譯時，下列程式碼範例會產生 C4312：  
  
```  
// C4312.cpp  
// compile by using: cl /W1 /LD C4312.cpp  
void* f(int i) {  
   return (void*)i;   // C4312 for 64-bit targets  
}  
  
void* f2(__int64 i) {  
   return (void*)i;   // OK  
}  
```