---
title: 編譯器錯誤 C3298 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3298
dev_langs:
- C++
helpviewer_keywords:
- C3298
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a67e155fb6cf0eab1ea085839d075d4d835de101
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250872"
---
# <a name="compiler-error-c3298"></a>編譯器錯誤 C3298
'constraint_1': 無法將 'constraint_2' 當做條件約束使用，因為 'constraint_2' 具有 ref 條件約束，而且 'constraint_1' 具有值條件約束  
  
 您不能指定條件約束的互斥特性。 例如，泛型類型參數不能同時限制為實值類型和參考類型。  
  
 如需詳細資訊，請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3298。  
  
```  
// C3298.cpp  
// compile with: /clr /c   
generic<class T, class U>  
where T : ref class  
where U : T, value class   // C3298  
public ref struct R {};  
```