---
title: 編譯器錯誤 C2061 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4d4b018dbab16e8e376a3331a85d0f1b1004f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2061"></a>編譯器錯誤 C2061
語法錯誤： 識別項 'identifier'  
  
 編譯器會發現未預期的識別項。 請確定`identifier`宣告再使用它。  
  
 初始設定式可能會放在括弧之中。 若要避免這個問題，括號括住的宣告子，或讓它`typedef`。  
  
 當編譯器偵測到為類別樣板引數; 運算式時，可能也會造成這個錯誤使用[typename](../../cpp/typename.md)告知編譯器為型別。  
  
 下列範例會產生 C2061:  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 如果您傳遞至執行個體名稱，就會發生 C2061 [typeid](../../windows/typeid-cpp-component-extensions.md):  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```