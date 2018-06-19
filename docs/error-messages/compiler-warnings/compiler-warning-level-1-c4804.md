---
title: 編譯器警告 （層級 1） C4804 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 677899230b2475c80f9bdd461a0c79740c4d3bec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286977"
---
# <a name="compiler-warning-level-1-c4804"></a>編譯器警告 (層級 1) C4804
'operation': 不安全的類型 'bool' 作業中使用  
  
 當您使用這項警告是針對`bool`變數或非預期的方式中的值。 如果您使用運算子，例如負值的一元運算子，例如，產生 C4804 (**-**) 或補充運算子 (`~`)。 編譯器會評估運算式。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4804:  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```