---
title: 編譯器錯誤 C3633 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3633
dev_langs:
- C++
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 341123f51a065cc8dcd43425f65b21edaf00abbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3633"></a>編譯器錯誤 C3633
無法將 'member' 定義為 managed 'type' 的成員  
  
CLR 參考類別資料成員不可為非 POD c + + 類型。  您可以只執行個體化 POD 原生類型中的 CLR 型別。  例如，POD 類型不能包含複製建構函式或指派運算子。  
  
## <a name="example"></a>範例  
下列範例會產生 C3633。  
  
```  
// C3633.cpp  
// compile with: /clr /c  
#pragma warning( disable : 4368 )  
  
class A1 {  
public:  
   A1() { II = 0; }  
   int II;  
};  
  
ref class B {  
public:  
   A1 a1;   // C3633  
   A1 * a2;   // OK  
   B() : a2( new A1 ) {}  
    ~B() { delete a2; }  
};  
```  
