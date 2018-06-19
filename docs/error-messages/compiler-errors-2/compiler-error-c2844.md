---
title: 編譯器錯誤 C2844 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2844
dev_langs:
- C++
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a45e4a94e3d474be670f822d56a7c080f25693c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247305"
---
# <a name="compiler-error-c2844"></a>編譯器錯誤 C2844
'member': 不可以是成員的介面 'interface'  
  
 [介面類別](../../windows/interface-class-cpp-component-extensions.md)不能包含資料成員，除非它也是屬性。  
  
 介面中不允許的屬性或成員函式以外的任何項目。 此外，不允許建構函式、 解構函式和運算子。  
  
 下列範例會產生 C2844:  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
