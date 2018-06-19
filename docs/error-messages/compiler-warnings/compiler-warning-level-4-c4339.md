---
title: 編譯器警告 （層級 4） C4339 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4339
dev_langs:
- C++
helpviewer_keywords:
- C4339
ms.assetid: 5b83353d-7777-4afb-8476-3c368349028c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b94d6a059c1c04eeae04bf917a84836c0354197e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295791"
---
# <a name="compiler-warning-level-4-c4339"></a>編譯器警告 (層級 4) C4339
'type'：偵測到在 WinRT 或 CLR 中繼資料中使用未定義的類型 - 使用此類型可能造成執行階段例外狀況  
  
 未在 Windows 執行階段或 Common Language Runtime 編譯的程式碼中定義類型。 定義要避免可能的執行階段例外狀況的類型。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 下列範例會產生 C4339，並示範如何修正此問題：  
  
```  
// C4339.cpp  
// compile with: /W4 /clr /c  
// C4339 expected  
#pragma warning(default : 4339)  
  
// Delete the following line to resolve.  
class A;  
  
// Uncomment the following line to resolve.  
// class A{};  
  
class X {  
public:  
   X() {}  
  
   virtual A *mf() {  
      return 0;  
   }  
};  
  
X * f() {  
   return new X();  
}  
```