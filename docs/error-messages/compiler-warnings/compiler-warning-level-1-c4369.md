---
title: 編譯器警告 （層級 1） C4369 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63445f0713b43ce7fde418ebd9d65403965c07ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276525"
---
# <a name="compiler-warning-level-1-c4369"></a>編譯器警告 (層級 1) C4369
'列舉值': 列舉值 'value' 無法表示為 'type'，值為 'new_value'  
  
 列舉值必須大於最大的值，指定基礎類型計算出來。  這會造成溢位，編譯器將列舉值包裝到最低的可能值類型。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4369。  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```