---
title: "編譯器錯誤 C3519 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3519
dev_langs:
- C++
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c655c8ba0513bcf25d5bc9666d65352a7f587374
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3519"></a>編譯器錯誤 C3519
'invalid_param': 對 embedded_idl 屬性無效的參數  
  
 參數傳遞給`embedded_idl`屬性[#import](../../preprocessor/hash-import-directive-cpp.md)，但編譯器無法辨認的參數。  
  
 允許的唯一參數`embedded_idl`是`emitidl`和`no_emitidl`。  
  
 下列範例會產生 C3519:  
  
```  
// C3519.cpp  
// compile with: /LD  
[module(name="MyLib2")];  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")     
// C3519  
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")     
// OK  
```
