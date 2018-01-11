---
title: "呼叫範例： 函式原型和呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: afdc7d91e11936ebfd1775477f8c684ae4ff6d62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="calling-example-function-prototype-and-call"></a>呼叫範例：函式原型和呼叫
## <a name="microsoft-specific"></a>Microsoft 特定的  
 下列範例示範使用各種呼叫慣例執行函式呼叫的結果。  
  
 這個範例是以下列函式架構為基礎。 以適當的呼叫慣例取代 `calltype`。  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 如需詳細資訊，請參閱[呼叫結果範例](../cpp/results-of-calling-example.md)。  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)