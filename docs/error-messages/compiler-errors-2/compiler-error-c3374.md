---
title: 編譯器錯誤 C3374
ms.date: 11/04/2016
f1_keywords:
- C3374
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
ms.openlocfilehash: 4b00b1cea8ac462c82c11d9f5b207706af74959c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022628"
---
# <a name="compiler-error-c3374"></a>編譯器錯誤 C3374

無法取得 'function' 的位址，除非建立委派執行個體

除了建立委派執行個體之外，已在內容中取得函式的位址。

下列範例會產生 C3374：

```
// C3374.cpp
// compile with: /clr
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      System::Console::WriteLine("in func1 {0}", i);
   }
};

int main() {
   &A::func1;   // C3374

   // OK
   A ^ a = gcnew A;
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);
}
```

## <a name="see-also"></a>另請參閱

[HOW TO：定義和使用委派 (C + + /cli CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)