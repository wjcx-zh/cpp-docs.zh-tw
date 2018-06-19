---
title: 編譯器錯誤 C2469 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2469
dev_langs:
- C++
helpviewer_keywords:
- C2469
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37decb55a2f24f7f29d28519e2f87eba90ff56bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197269"
---
# <a name="compiler-error-c2469"></a>編譯器錯誤 C2469
'operator': 無法配置 'type' 物件  
  
 傳遞的運算子具有無效的類型。  
  
 下列範例會產生 C2469：  
  
```  
// C2469.cpp  
int main() {  
   int *i = new void;   // C2469  
   int *i = new int;   // OK  
}  
```