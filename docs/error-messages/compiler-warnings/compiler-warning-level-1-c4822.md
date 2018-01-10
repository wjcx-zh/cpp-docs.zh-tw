---
title: "編譯器警告 （層級 1） C4822 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4822
dev_langs: C++
helpviewer_keywords: C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 89ed0dc851726b7b543ed2b8e1a319cc2ac6756e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4822"></a>編譯器警告 (層級 1) C4822
'member: 區域類別成員函式沒有主體  
  
 區域類別成員函式已宣告但未定義於類別中。 若要使用區域類別成員函式，您必須在類別中定義它。 您不能在類別中宣告它，但在類別外定義它。  
  
 區域類別成員函式的任何類別外定義會發生錯誤。  
  
 下列範例會產生 C4822：  
  
```  
// C4822.cpp  
// compile with: /W1  
int main() {  
   struct C {  
      void func1(int);   // C4822  
      // try the following line instead  
      // void func1(int){}  
  };  
}  
```