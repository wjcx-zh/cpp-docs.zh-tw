---
title: "編譯器錯誤 C3380 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3380
dev_langs:
- C++
helpviewer_keywords:
- C3380
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8789889ab0d9ebe93941a438c286ed718ac4721
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3380"></a>編譯器錯誤 C3380
'class' : 組件存取規範無效 - 只能使用 'public' 或 'private'  
  
 套用至 Managed 類別或結構時， [public](../../cpp/public-cpp.md) 和 [private](../../cpp/private-cpp.md) 關鍵字會指出類別是否將透過組件中繼資料公開。 只有 `public` 或 `private` 能夠套用至以 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)所編譯程式中的類別。  
  
 `ref`和`value`關鍵字搭配使用時[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，指出類別 managed (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))。  
  
 下列範例會產生 C3380：  
  
```  
// C3380_2.cpp  
// compile with: /clr  
protected ref class A {   // C3380  
// try the following line instead  
// ref class A {  
public:  
   static int i = 9;  
};  
  
int main() {  
   A^ myA = gcnew A;  
   System::Console::WriteLine(myA->i);  
}  
```  
