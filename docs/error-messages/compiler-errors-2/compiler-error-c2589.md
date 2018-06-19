---
title: 編譯器錯誤 C2589 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c15589358979f554a9c17114f7d78b05dd83c472
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230749"
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