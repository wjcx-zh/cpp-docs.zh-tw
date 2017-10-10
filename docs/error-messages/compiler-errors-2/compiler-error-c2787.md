---
title: "編譯器錯誤 C2787 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2787
dev_langs:
- C++
helpviewer_keywords:
- C2787
ms.assetid: 34cb57e6-cafe-4ce7-bcc6-53d194629bd0
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 71924ae6e24eba04e27ec366ef73dedc2fa65263
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
