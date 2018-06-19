---
title: 編譯器錯誤 C3297 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3297
dev_langs:
- C++
helpviewer_keywords:
- C3297
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5afdf54e7a335dda86a4046a01b31875a0c91575
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249362"
---
# <a name="compiler-error-c3297"></a>編譯器錯誤 C3297
'constraint_2': 因為 'constraint_1' 有值條件約束，所以 'constraint_1' 不能用做條件約束  
  
 值類別已密封。 如果條件約束是值類別，它絕對不會衍生其他的條件約束。  
  
 如需詳細資訊，請參閱[泛型型別參數的條件約束 (C + + /CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3297。  
  
```  
// C3297.cpp  
// compile with: /clr /c  
generic<class T, class U>  
where T : value class  
where U : T   // C3297  
public ref struct R {};  
```