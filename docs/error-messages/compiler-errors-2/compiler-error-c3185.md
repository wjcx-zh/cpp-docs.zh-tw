---
title: 編譯器錯誤 C3185 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3185
dev_langs:
- C++
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce6eea7c9a40f9dd38bf6892995eaa52ac540de7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3185"></a>編譯器錯誤 C3185
Managed 或 WinRT 類型 'type' 上使用 'typeid'，請改用 'operator'  
  
 您不能套用[typeid](../../cpp/typeid-operator.md)運算子，在 managed 或 WinRT 類型; 請改用[typeid](../../windows/typeid-cpp-component-extensions.md)改為。  
  
 下列範例會產生 C3185，並示範如何修正此問題：  
  
```  
// C3185a.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
  
int main() {  
   Derived ^ pd = gcnew Derived;  
   Base ^pb = pd;  
   const type_info & t1 = typeid(pb);   // C3185  
   System::Type ^ MyType = Base::typeid;   // OK  
};  
```  
