---
title: "編譯器錯誤 C3062 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fa921df80f0740387217ec9b295cfa90e089d54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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