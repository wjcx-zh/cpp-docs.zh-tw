---
title: "編譯器錯誤 C2589 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2589
dev_langs: C++
helpviewer_keywords: C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5301caf0b52e61000a804e1d73b76343a8b7b2eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2589"></a>編譯器錯誤 C2589
'identifier': 不合法的語彙基元，在右邊 ':: '  
  
 如果類別、 結構或等位名稱會顯示在左邊的範圍解析運算子 （雙冒號），在右邊的語彙基元必須是類別、 結構或等位成員。 否則，任何全域識別項可以出現在右邊。  
  
 範圍解析運算子無法多載。  
  
 下列範例會產生 C2589:  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```