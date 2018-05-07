---
title: 編譯器錯誤 C3753 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3753
dev_langs:
- C++
helpviewer_keywords:
- C3753
ms.assetid: a5b99e28-796c-4107-a673-97c2ae3bb2b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0d9cb2db2729e5ccb1787e2505fdf0aed1f7a12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3753"></a>編譯器錯誤 C3753
不允許泛型屬性。  
  
 泛型參數清單只能出現在受管理的類別、 結構或函式。  
  
 如需詳細資訊，請參閱[泛型](../../windows/generics-cpp-component-extensions.md)和[屬性](../../windows/property-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3753。  
  
```  
// C3753.cpp  
// compile with: /clr /c  
ref struct A {  
   generic <typename T>  
   property int i;   // C3753 error  
};  
```