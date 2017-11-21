---
title: "編譯器錯誤 C2583 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2583
dev_langs: C++
helpviewer_keywords: C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 924a370a59fff0e118b76e52e17d44b3b2268103
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2583"></a>編譯器錯誤 C2583
'identifier': 'const/volatile' 'this' 指標不合法的建構函式/解構函式  
  
 建構函式或解構函式宣告`const`或`volatile`。 這是不允許的。  
  
 下列範例會產生 C2583:  
  
```  
// C2583.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
   A() const;   // C2583  
  
   // try the following line instead  
   // A();  
};  
```