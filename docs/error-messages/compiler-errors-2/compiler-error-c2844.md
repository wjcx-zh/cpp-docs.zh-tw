---
title: "編譯器錯誤 C2844 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2844
dev_langs:
- C++
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3353a6dbacaca2779bb4feffe55958baf0c944e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
