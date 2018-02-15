---
title: "如何： 封送處理內嵌指標使用 PInvoke |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cd2717e5ffc5dc25f7a98f679a23d6f97fd335a5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>如何：使用 PInvoke 封送處理內嵌指標
可以呼叫 unmanaged Dll 中實作的函式，從 managed 程式碼使用平台叫用 (P/Invoke) 的功能。 如果無法使用 DLL 的原始程式碼，P/Invoke 是互通的唯一選項。 不過，不同於其他.NET 語言中，Visual c + + 提供 P/Invoke 的替代方案。 如需詳細資訊，請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)和[如何： 封送處理內嵌指標使用 c + + Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
## <a name="example"></a>範例  
 將結構傳遞至原生程式碼需要建立的受管理的結構，這是對原生結構等方面的資料配置。 不過，結構，其中包含指標需要進行特殊處理。 原生結構中每個內嵌指標、 結構的受管理的版本應該包含的執行個體<xref:System.IntPtr>型別。 此外，記憶體的這些執行個體，就必須明確配置，初始化，且發行使用<xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>， <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>，和<xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A>方法。  
  
 下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組是可定義接受結構稱為 ListString 包含指標的函式和函式，呼叫 TakesListStruct DLL。 受管理的模組是命令列應用程式可匯入 TakesListStruct 函式，以及定義稱為 MListStruct 相當於原生 ListStruct 不同之處在於雙 * 表示與結構<xref:System.IntPtr>執行個體。 在呼叫前 TakesListStruct，main 函式配置，並初始化這個欄位參考的記憶體。  
  
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
  
 請注意，DLL 的任何部分公開給 managed 程式碼使用的傳統 #include 指示詞。 事實上，DLL 會在執行階段存取，因此問題函式匯入與<xref:System.Runtime.InteropServices.DllImportAttribute>將不會在編譯時期偵測。  
  
## <a name="see-also"></a>請參閱  
 [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)