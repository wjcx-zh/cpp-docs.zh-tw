---
title: "編譯器錯誤 C2663 | Microsoft Docs"
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
  - "C2663"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2663"
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2663
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 數個多載沒有 'this' 指標的合法轉換  
  
 編譯器無法將 `this` 轉換成任何多載成員函式版本。  
  
 這項錯誤可能是因在 `const` 物件上叫用非 `const` 成員函式所致。可能的解決方案：  
  
1.  將 `const` 從物件宣告中移除。  
  
2.  將 `const` 加入至其中一個成員函式多載。  
  
 下列範例會產生 C2663：  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```