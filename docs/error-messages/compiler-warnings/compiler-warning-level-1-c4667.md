---
title: "編譯器警告 (層級 1) C4667 | Microsoft Docs"
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
  - "C4667"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4667"
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4667
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 沒有定義符合強制具現化 \(instantiation\) 的函式樣板  
  
 您不能具現化尚未被宣告的函式樣板。  
  
 下列範例將產生 C4667：  
  
```  
// C4667a.cpp  
// compile with: /LD /W1  
template  
void max(const int &, const int &); // C4667 expected  
```  
  
 若要避免此警告，首先要宣告函式樣板：  
  
```  
// C4667b.cpp  
// compile with: /LD  
// Declare the function template  
template<typename T>  
const T &max(const T &a, const T &b) {  
   return (a > b) ? a : b;  
}  
// Then forcibly instantiate it with a desired type ... i.e. 'int'  
//  
template  
const int &max(const int &, const int &);  
```