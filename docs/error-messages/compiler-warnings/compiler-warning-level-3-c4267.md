---
title: "編譯器警告 (層級 3) C4267 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4267"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4267"
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4267
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': 將 'size\_t' 轉換為 'type'，資料可能遺失  
  
 編譯器偵測到從 `size_t` 轉換成較小的類型。  
  
 若要修正這項警告，請使用 `size_t`，而不是 `type`。  或者，使用至少與 `size_t` 一樣大的整數類型。  
  
## 範例  
 下列範例會產生 C4267：  
  
```  
// C4267.cpp  
// compile by using: cl /W4 C4267.cpp  
void Func1(short) {}  
void Func2(int) {}  
void Func3(long) {}  
void Func4(size_t) {}  
  
int main() {  
   size_t bufferSize = 10;  
   Func1(bufferSize);   // C4267 for all platforms  
   Func2(bufferSize);   // C4267 only for 64-bit platforms  
   Func3(bufferSize);   // C4267 only for 64-bit platforms  
   Func4(bufferSize);   // OK for all platforms  
}  
```