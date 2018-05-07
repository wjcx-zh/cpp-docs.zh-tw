---
title: 編譯器錯誤 C2461 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2461
dev_langs:
- C++
helpviewer_keywords:
- C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47aee3122dad3e875cf58d5a41bcadda297e1463
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2461"></a>編譯器錯誤 C2461
  
> '*類別*': 建構函式語法遺漏型式參數  
  
 類別的建構函式未指定任何型式參數。 建構函式宣告必須指定型式參數清單。 清單可以是空的。  
  
若要修正此問題，請新增一組括弧的宣告之後*類別*:: **類別*。  
  
## <a name="example"></a>範例  
  
下列範例會示範如何修正問題 C2461:  
  
```cpp  
// C2461.cpp  
// compile with: /c  
class C {  
   C::C;     // C2461  
   C::C();   // OK  
};  
```