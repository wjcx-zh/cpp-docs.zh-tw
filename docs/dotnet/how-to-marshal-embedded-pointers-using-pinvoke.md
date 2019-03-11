---
title: HOW TO：封送處理內嵌指標使用 PInvoke
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: 943a1a2784a37353157cd38da7ebdc9827006fe5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738752"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>HOW TO：封送處理內嵌指標使用 PInvoke

從 managed 程式碼使用平台叫用 (P/Invoke) 的功能，可以呼叫 unmanaged Dll 中實作的函式。 如果無法使用 DLL 的原始程式碼，P/Invoke 是交互操作的唯一選項。 不過，不同於其他.NET 語言，Visual c + + 提供 P/Invoke 的替代方案。 如需詳細資訊，請參閱 <<c0> [ 使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)和[How to:封送處理內嵌指標使用 c + + Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。

## <a name="example"></a>範例

將結構傳遞至原生程式碼需要，會建立受管理的結構，等於是根據資料配置的原生結構。 不過，結構，其中包含指標需要特殊處理。 對於原生結構中每個內嵌指標，結構的 managed 的版本應該包含的執行個體<xref:System.IntPtr>型別。 此外，記憶體為這些執行個體都必須明確配置，初始化，而且使用<xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>， <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>，和<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>方法。

下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組是定義接受結構，稱為 ListString 包含指標的函式和呼叫 TakesListStruct 函式的 DLL。 受管理的模組是命令列應用程式匯入 TakesListStruct 函式，並定義結構，稱為 MListStruct，相當於原生 ListStruct 不同之處在於雙精度浮點數 * 代表與<xref:System.IntPtr>執行個體。 在呼叫前 TakesListStruct，main 函式配置，並初始化此欄位會參考的記憶體。

```cpp
// TraditionalDll6.cpp
// compile with: /EHsc /LD
#include <stdio.h>
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct ListStruct {
   int count;
   double* item;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API void TakesListStruct(ListStruct);
}

void TakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}
```

```cpp
// EmbeddedPointerMarshalling.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MListStruct {
   int count;
   IntPtr item;
};

value struct TraditionalDLL {
    [DllImport("TraditionalDLL6.dll")]
   static public void TakesListStruct(MListStruct);
};

int main() {
   array<double>^ parray = gcnew array<double>(10);
   Console::WriteLine("[managed] count = {0}", parray->Length);

   Random^ r = gcnew Random();
   for (int i=0; i<parray->Length; i++) {
      parray[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);
   }

   int size = Marshal::SizeOf(double::typeid);
   MListStruct list;
   list.count = parray->Length;
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);

   for (int i=0; i<parray->Length; i++) {
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);
      Marshal::StructureToPtr(parray[i], t, false);
   }

   TraditionalDLL::TakesListStruct( list );
   Marshal::FreeCoTaskMem(list.item);
}
```

請注意沒有部分的 dll 會使用傳統的 managed 程式碼以 #include 指示詞。 事實上，DLL 會在執行階段存取，因此問題函式匯入與<xref:System.Runtime.InteropServices.DllImportAttribute>將不會在編譯時期偵測。

## <a name="see-also"></a>另請參閱

[在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
