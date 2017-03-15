---
title: "編譯器錯誤 C2825 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2825"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2825"
ms.assetid: c832f1c1-5184-4fc2-9356-12b21daa7af3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2825
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

var : 後面接 '::' 時必須是類別或命名空間  
  
 嘗試形成限定名稱 \(Qualified Name\) 失敗。  
  
 例如，請確定您的程式碼不包含函式名稱是以 :: 開頭的函式宣告。  
  
## 範例  
 下列範例會產生 C2825：  
  
```  
// C2825.cpp  
typedef int i;  
int main() {  
   int* p = new int;  
   p->i::i();   // C2825  
   // try the following line instead  
   // p->i::~i();  
}  
```