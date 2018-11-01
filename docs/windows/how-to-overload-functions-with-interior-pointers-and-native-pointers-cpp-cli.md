---
title: 如何：多載具有內部指標與原生指標的函式 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: e7c3ca576b2f3d961b4720cc6175103c54316015
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666361"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>如何：多載具有內部指標與原生指標的函式 (C++/CLI)

可以多載函式，根據參數型別為內部指標或原生指標。

> [!IMPORTANT]
> `/clr` 編譯器選項支援這項語言功能，`/ZW` 編譯器選項則不支援。

## <a name="example"></a>範例

### <a name="code"></a>程式碼

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output
in f( int* pi )
in f( interior_ptr<int> pi )
```

## <a name="see-also"></a>另請參閱

[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)