---
title: 編譯器錯誤 C3381 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a27961694bc5fad4080d8aceaf2f1cb65404319c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3381"></a>編譯器錯誤 C3381
'assembly': 組件存取規範只有會提供以 /clr 選項編譯程式碼  
  
 原生類型才能可見組件外部的但您只能指定原生類型中的組件存取 **/clr**編譯。  
  
 如需詳細資訊，請參閱[類型可視性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3381。  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```