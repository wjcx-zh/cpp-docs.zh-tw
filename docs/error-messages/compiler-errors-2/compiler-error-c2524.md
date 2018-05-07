---
title: 編譯器錯誤 C2524 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2524
dev_langs:
- C++
helpviewer_keywords:
- C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b21a907de69291c6d7fbc23f3ea093271a1ad3b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2524"></a>編譯器錯誤 C2524
'解構函式': 解構函式/完成項必須有 'void' 參數清單  
  
 解構函式或完成項必須不是參數清單[void](../../cpp/void-cpp.md)。 不允許其他參數類型。  
  
## <a name="example"></a>範例  
 下列程式碼會重現 C2524。  
  
```  
// C2524.cpp  
// compile with: /c  
class A {  
   A() {}  
   ~A(int i) {}    // C2524  
   // try the following line instead  
   // ~A() {}  
};  
```  
  
## <a name="example"></a>範例  
 下列程式碼會重現 C2524。  
  
```  
// C2524_b.cpp  
// compile with: /clr /c  
ref struct I1 {  
protected:  
   !I1(int i);   // C2524  
   // try the following line instead  
   // !I1();  
};  
```