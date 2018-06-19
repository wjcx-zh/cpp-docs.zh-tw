---
title: 編譯器錯誤 C3277 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3277
dev_langs:
- C++
helpviewer_keywords:
- C3277
ms.assetid: 8ac5f476-e30c-4879-92c6-f03cdbd74045
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd38ccc8a4f812a458073c429d83cebe5dff151b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250012"
---
# <a name="compiler-error-c3277"></a>編譯器錯誤 C3277
無法在受管理的 'type' 內部定義 unmanaged 的列舉 'enum'  
  
 列舉型別內的 managed 型別定義不正確。  
  
 下列範例會產生 C3277:  
  
```  
// C3277a.cpp  
// compile with: /clr  
ref class A  
{  
   enum E {e1,e2};   // C3277  
   // try the following line instead  
   // enum class E {e1,e2};  
};  
  
int main()  
{  
}  
```  
