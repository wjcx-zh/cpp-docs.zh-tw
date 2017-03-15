---
title: "編譯器錯誤 C2868 | Microsoft Docs"
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
  - "C2868"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2868"
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2868
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : using 宣告的不合法語法; 必須是限定名稱  
  
 [using 宣告](../../cpp/using-declaration.md)需要[限定名稱](http://msdn.microsoft.com/zh-tw/3fefb16d-8120-4627-8b3f-3d90fbdcd1df) \(Qualified Name\)。  
  
 下列範例會產生 C2868：  
  
```  
// C2868.cpp  
class X {  
public:  
   int i;  
};  
  
class Y : X {  
public:  
   using X::i;   // OK  
};  
  
int main() {  
   using X;   // C2868  
}  
```