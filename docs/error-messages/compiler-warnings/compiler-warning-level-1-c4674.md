---
title: 編譯器警告 （層級 1） C4674 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ede4ac8f8d0af94d998914b8a434cd8b2a9f482
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4674"></a>編譯器警告 (層級 1) C4674
'method' 必須宣告為 'static'，而且只能有一個參數  
  
轉換運算子的簽章不正確。 此方法不會視為使用者定義的轉換。 如需有關定義運算子的詳細資訊，請參閱[使用者定義的運算子 (C + + CLI)](../../dotnet/user-defined-operators-cpp-cli.md)和[使用者定義轉換 (C + + CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4674。  
  
```  
// C4674.cpp  
// compile with: /clr /WX /W1 /LD  
ref class G {  
   int op_Implicit(int i) {   // C4674  
      return 0;  
   }  
};  
```  
