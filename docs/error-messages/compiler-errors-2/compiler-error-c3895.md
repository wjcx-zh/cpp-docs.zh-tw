---
title: 編譯器錯誤 C3895 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3895
dev_langs:
- C++
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69139ed5a1b12d3159ce9fbf3b967cbc27e9264d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3895"></a>編譯器錯誤 C3895
'var': 型別資料成員不可為 'volatile'  
  
 某些類型的資料成員，例如[常值](../../windows/literal-cpp-component-extensions.md)或[initonly](../../dotnet/initonly-cpp-cli.md)，不能[volatile](../../cpp/volatile-cpp.md)。  
  
 下列範例會產生 C3895:  
  
```  
// C3895.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly  
   volatile int data_var2;   // C3895  
};  
```