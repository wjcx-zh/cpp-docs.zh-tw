---
title: "編譯器錯誤 C2357 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2357
dev_langs:
- C++
helpviewer_keywords:
- C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b3804f0ee55284aabcd46b0f45c557ccc79cbb8a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2357"></a>編譯器錯誤 C2357
'identifier': 必須是 'type' 類型的函式  
  
 您的程式碼會宣告一個版本的`atexit`由編譯器在內部宣告不符合版本的函式。 宣告`atexit`，如下所示：  
  
```  
int __cdecl atexit(void (__cdecl *)());  
```  
  
 如需詳細資訊，請參閱[init_seg](../../preprocessor/init-seg.md)。  
  
 下列範例會產生 C2357:  
  
```  
// C2357.cpp  
// compile with: /c  
// C2357 expected  
#pragma warning(disable : 4075)  
// Uncomment the following line to resolve.  
// int __cdecl myexit(void (__cdecl *)());  
#pragma init_seg(".mine$m",myexit)  
```
