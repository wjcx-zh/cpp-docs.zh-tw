---
title: "編譯器警告 （層級 1） C4584 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4584
dev_langs: C++
helpviewer_keywords: C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba427de26d07851c5bf2a2dd3f599c4cbe7afc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4584"></a>編譯器警告 (層級 1) C4584
'class1': 基底類別 'class2' 已經是 'class3 移' 基底類別  
  
 您所定義的類別繼承自兩個類別，從另一個繼承。 例如:   
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 在此情況下，會發出警告類別 C 上因為它同時繼承自類別 A 和 B，也會繼承自類別 a 類別這個警告會當做提醒您必須完整限定使用來自這些基底類別的成員，或將產生編譯器錯誤，因為對於哪個類別成員參考模稜兩可。