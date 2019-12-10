---
title: 如何：使用 C++ Interop 封送處理內嵌指標
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
ms.openlocfilehash: 972d7a9c09100c35cb0bf527efbd0884c909c46d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988181"
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>如何：使用 C++ Interop 封送處理內嵌指標

下列程式碼範例會使用[managed、非](../preprocessor/managed-unmanaged.md)受控 #pragma 指示詞，在同一個檔案中執行 managed 和非受控函式，但如果在個別的檔案中定義，則這些函式會以相同的方式進行交互作用。 僅包含非受控函式的檔案不需要使用[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)進行編譯。

## <a name="example"></a>範例

下列範例示範如何從 managed 函式呼叫接受包含指標之結構的非受控函式。 Managed 函式會建立結構的實例，並使用 new 關鍵字（而不是[ref new、gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)關鍵字）初始化內嵌指標。 因為這會在原生堆積上配置記憶體，所以不需要釘選陣列來抑制垃圾收集。 不過，必須明確刪除記憶體，以避免記憶體流失。

```cpp
// marshal_embedded_pointer.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

// unmanaged struct
struct ListStruct {
   int count;
   double* item;
};

#pragma unmanaged

void UnmanagedTakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}

#pragma managed

int main() {
   ListStruct list;
   list.count = 10;
   list.item = new double[list.count];

   Console::WriteLine("[managed] count = {0}", list.count);
   Random^ r = gcnew Random(0);
   for (int i=0; i<list.count; i++) {
      list.item[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);
   }

   UnmanagedTakesListStruct( list );
   delete list.item;
}
```

```Output
[managed] count = 10
array[0] = 72.624326996796
array[1] = 81.7325359590969
array[2] = 76.8022689394663
array[3] = 55.8161191436537
array[4] = 20.6033154021033
array[5] = 55.8884794618415
array[6] = 90.6027066011926
array[7] = 44.2177873310716
array[8] = 97.754975314138
array[9] = 27.370445768987
[unmanaged] count = 10
array[0] = 72.624327
array[1] = 81.732536
array[2] = 76.802269
array[3] = 55.816119
array[4] = 20.603315
array[5] = 55.888479
array[6] = 90.602707
array[7] = 44.217787
array[8] = 97.754975
array[9] = 27.370446
```

## <a name="see-also"></a>請參閱

[使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
