---
title: "編譯器錯誤 C2270 | Microsoft Docs"
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
  - "C2270"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2270"
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2270
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 不允許在非成員函式上使用修飾詞  
  
 使用了 [const](../../cpp/const-cpp.md)、[volatile](../../cpp/volatile-cpp.md) 或其他記憶體模型修飾詞 \(Modifier\) 來宣告非成員函式。  
  
 下列範例會產生 C2270：  
  
```  
// C2270.cpp  
// compile with: /c  
void func1(void) const;   // C2270, nonmember function  
  
void func2(void);  
  
class CMyClass {  
public:  
   void func2(void) const;  
};  
```