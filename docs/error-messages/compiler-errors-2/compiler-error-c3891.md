---
title: 編譯器錯誤 C3891 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3891
dev_langs:
- C++
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 021f19d50d0b83c9526956684737ad23fea9fb01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272704"
---
# <a name="compiler-error-c3891"></a>編譯器錯誤 C3891
'var': 常值資料成員不能做為左值  
  
 A[常值](../../windows/literal-cpp-component-extensions.md)變數是 const，而在宣告中初始化之後，就無法變更其值。  
  
 下列範例會產生 C3891:  
  
```  
// C3891.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   Y1::staticConst = 0;   // C3891  
}  
```