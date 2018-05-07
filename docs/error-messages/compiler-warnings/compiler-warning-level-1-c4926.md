---
title: 編譯器警告 （層級 1） C4926 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4926
dev_langs:
- C++
helpviewer_keywords:
- C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 527c03d4f71048064c2120f7cfa9730de198fd46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4926"></a>編譯器警告 (層級 1) C4926
'identifier': 已定義符號：忽略屬性  
  
 找到向前宣告，但具有相同名稱的屬性化結構已存在。 向前宣告的屬性會被忽略。  
  
 下列範例會產生 C4926：  
  
```  
// C4926.cpp  
// compile with: /W1  
[module(name="MyLib")];  
  
[coclass]  
struct a {  
};  
  
[coclass]  
struct a;   // C4926  
  
int main() {  
}  
```