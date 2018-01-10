---
title: "編譯器錯誤 C2461 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2461
dev_langs: C++
helpviewer_keywords: C2461
ms.assetid: e64ba651-f441-4fdb-b5cb-4209bbbe4db4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e5e1593e37bd3a02897d023e308593e23d3d73b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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