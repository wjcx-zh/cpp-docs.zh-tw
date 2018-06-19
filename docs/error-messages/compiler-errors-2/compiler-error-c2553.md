---
title: 編譯器錯誤 C2553 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cfb09f2701b418ab5570641a78c465ff72ed943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232530"
---
# <a name="compiler-error-c2553"></a>編譯器錯誤 C2553
'base_function': 覆寫虛擬函式傳回類型不同於 'override_function'  
  
 在衍生類別中的函式嘗試覆寫虛擬函式中的基底類別，但在衍生的類別函式沒有基底類別函式相同的傳回型別。  覆寫函式簽章必須符合覆寫的函式簽章。  
  
 下列範例會產生 C2553:  
  
```  
// C2553.cpp  
// compile with: /clr /c  
ref struct C {  
   virtual void f();  
};  
  
ref struct D : C {  
   virtual int f() override ;   // C2553   
  
   // try the following line instead  
   // virtual void f() override;  
};  
```