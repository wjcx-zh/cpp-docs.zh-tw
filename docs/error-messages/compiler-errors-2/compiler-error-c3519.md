---
title: 編譯器錯誤 C3519 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3519
dev_langs:
- C++
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 740fef32484164e7439335686adce0a4aa8027f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257194"
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