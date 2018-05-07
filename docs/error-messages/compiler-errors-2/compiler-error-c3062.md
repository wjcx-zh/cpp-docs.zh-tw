---
title: 編譯器錯誤 C3062 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da507511cb5f091d5d9432bbfeb36951e3f43c6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3062"></a>編譯器錯誤 C3062
'enum': 列舉值需要值，因為基礎類型是 'type'  
  
 您可以指定列舉的基礎型別。 不過，某些類型需要您將值指派給每個列舉值。  
  
 如需有關列舉的詳細資訊，請參閱[列舉類別](../../windows/enum-class-cpp-component-extensions.md)。  
  
 下列範例會產生 C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```