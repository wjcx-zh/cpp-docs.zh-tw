---
title: 編譯器錯誤 C3749 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3749
dev_langs:
- C++
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78de0c696123375c11e5c11e64223858b57451ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270771"
---
# <a name="compiler-error-c3749"></a>編譯器錯誤 C3749
'attribute': 自訂屬性不能在函式  
  
 自訂屬性不能在函式。 如需有關自訂屬性的詳細資訊，請參閱主題[屬性](../../windows/attribute.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3749:  
  
```  
// C3749a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref struct ABC : public Attribute {  
   ABC() {}  
};  
  
void f1() { [ABC]; };  // C3749  
```  
