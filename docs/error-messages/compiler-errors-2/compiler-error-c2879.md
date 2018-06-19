---
title: 編譯器錯誤 C2879 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2879
dev_langs:
- C++
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba1738da7d349ecafd9f10f31d8f05ac1f12df0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243159"
---
# <a name="compiler-error-c2879"></a>編譯器錯誤 C2879
'symbol': 只有現有命名空間可以由命名空間別名定義授與不同的名稱  
  
 無法建立[命名空間別名](../../cpp/namespaces-cpp.md#namespace_aliases)命名空間以外的符號。  
  
 下列範例會產生 C2879:  
  
```  
// C2879.cpp  
int main() {  
   int i;  
   namespace A = i;   // C2879 i is not a namespace  
}  
```