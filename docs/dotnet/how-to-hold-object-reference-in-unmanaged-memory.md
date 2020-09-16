---
title: 如何：在 Unmanaged 記憶體中存放物件參考
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 13d5bd37a0f5e0b065aecb8c5b264fb70685363f
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684504"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>如何：在 Unmanaged 記憶體中存放物件參考

您可以使用 gcroot <xref:System.Runtime.InteropServices.GCHandle> 來將 CLR 物件參考保存在非受控記憶體中。 或者，您也可以 `GCHandle` 直接使用。

## <a name="examples"></a>範例

```cpp
// hold_object_reference.cpp
// compile with: /clr
#include "gcroot.h"
using namespace System;

#pragma managed
class StringWrapper {

private:
   gcroot<String ^ > x;

public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      x = str;
   }

   void PrintString() {
      String ^ targetStr = x;
      Console::WriteLine("StringWrapper::x == {0}", targetStr);
   }
};
#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::x == ManagedString
```

`GCHandle` 提供在非受控記憶體中保存受管理物件參考的方法。  您可以使用 <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> 方法來建立受管理物件的不透明控制碼，並 <xref:System.Runtime.InteropServices.GCHandle.Free%2A> 加以釋放。 此外，此 <xref:System.Runtime.InteropServices.GCHandle.Target%2A> 方法可讓您從 managed 程式碼中的控制碼取得物件參考。

```cpp
// hold_object_reference_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed
class StringWrapper {
   IntPtr m_handle;
public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));
   }
   ~StringWrapper() {
      static_cast<GCHandle>(m_handle).Free();
   }

   void PrintString() {
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);
   }
};

#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::m_handle == ManagedString
```

## <a name="see-also"></a>另請參閱

[使用 c + + Interop (隱含 PInvoke) ](../dotnet/using-cpp-interop-implicit-pinvoke.md)
