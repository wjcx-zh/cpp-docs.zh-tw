---
title: "編譯器錯誤 C2272 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2272
dev_langs: C++
helpviewer_keywords: C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 305b0cd510c088f4731a8430959f76bb57ee33a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2272"></a>編譯器錯誤 C2272
'function': 靜態成員函式不允許修飾詞  
  
 A`static`宣告成員函式會與記憶體模型規範，例如[const](../../cpp/const-cpp.md)或[volatile](../../cpp/volatile-cpp.md)，而且這類修飾詞不會允許`static`成員函式。  
  
 下列範例會產生 C2272:  
  
```  
// C2272.cpp  
// compile with: /c  
class CMyClass {  
public:  
   static void func1() const volatile;   // C2272  func1 is static  
   void func2() const volatile;   // OK  
};  
```