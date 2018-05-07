---
title: 編譯器錯誤 C3309 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3309
dev_langs:
- C++
helpviewer_keywords:
- C3309
ms.assetid: 75ee16e3-7d4e-4c41-b3cb-64e9849c3aab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 390740c3a7083ede314f58a7bc68432c243583ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3309"></a>編譯器錯誤 C3309
'macro_name'：模組名稱不可為巨集或關鍵字  
  
 您傳遞給模組屬性的名稱屬性值不能是讓前置處理器擴充的符號，它必須是字串常值。  
  
 下例會產生 C3309：  
  
```  
// C3309.cpp  
#define NAME MyModule  
[module(name="NAME")];   // C3309  
// Try the following line instead  
// [module(name="MyModule")];  
[coclass]  
class MyClass {  
public:  
   void MyFunc();  
};  
  
int main() {  
}  
```