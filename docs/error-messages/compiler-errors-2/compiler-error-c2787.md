---
title: 編譯器錯誤 C2787 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2787
dev_langs:
- C++
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6b45d27c295b37d859d6451281f52c166dc1691
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2787"></a>編譯器錯誤 C2787
'identifier': 沒有 GUID 已經與此物件相關聯  
  
 [__Uuidof](../../cpp/uuidof-operator.md)運算子採用的使用者定義型別與附加的 GUID 或這類使用者定義型別的物件。 不具有 GUID 的使用者定義型別引數時，就會發生此錯誤。  
  
 下列範例會產生 C2787:  
  
```  
// C2787.cpp  
#include <windows.h>  
struct F {};  
  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) F2;  
  
int main() {  
   __uuidof(F);   // C2787  
   __uuidof(F2);   // OK  
}  
```