---
title: 編譯器警告 （層級 2） C4285 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4285
dev_langs:
- C++
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4366142c14ec77c1c344312e50e7295c71ca93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291696"
---
# <a name="compiler-warning-level-2-c4285"></a>編譯器警告 (層級 2) C4285
傳回型別 'identifier:: operator->' 是遞迴的如果套用使用中置標記法  
  
 指定**operator-> （)** 函式無法傳回的型別它被定義或為其定義的類型的參考。  
  
 下列範例會產生 C4285:  
  
```  
// C4285.cpp  
// compile with: /W2  
class C  
{  
public:  
    C operator->();   // C4285  
   // C& operator->();  C4285, also  
};  
  
int main()  
{  
}  
```