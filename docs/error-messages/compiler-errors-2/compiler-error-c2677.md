---
title: 編譯器錯誤 C2677 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2677
dev_langs:
- C++
helpviewer_keywords:
- C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 671be6d7e6acf252b774c4cd379fbc15267e4d94
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233158"
---
# <a name="compiler-error-c2677"></a>編譯器錯誤 C2677
二元 'operator': 沒有全域運算子找到其可接受類型 'type' （或沒有可接受的轉換）  
  
 若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。  
  
 下列範例會產生 C2677:  
  
```  
// C2677.cpp  
class C {  
public:  
   C(){}  
} c;  
  
class D {  
public:  
   D(){}  
   operator int(){return 0;}  
} d;  
  
int main() {  
   int i = 1 >> c;   // C2677  
   int j = 1 >> d;   // OK operator int() defined  
}  
```