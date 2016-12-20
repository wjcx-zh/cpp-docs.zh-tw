---
title: "如何：使用 PInvoke 封送處理內嵌指標 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料封送處理 [C++], 內嵌指標"
  - "內嵌指標 [C++]"
  - "Interop [C++], 內嵌指標"
  - "封送處理 [C++], 內嵌指標"
  - "平台叫用 [C++], 內嵌指標"
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 PInvoke 封送處理內嵌指標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用平台叫用 \(P\/Invoke\) 功能從 Managed 程式碼中呼叫實作在 Unmanaged DLL 中的函式。  如果沒有 DLL 的原始程式碼，則 P\/Invoke 是互通的唯一選擇。  不過，不同於其他 .NET 語言，Visual C\+\+ 提供了 P\/Invoke 的替代方案。  如需詳細資訊，請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)與[如何：使用 C\+\+ Interop 封送處理內嵌指標](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)。  
  
## 範例  
 將結構傳遞至原生 \(Native\) 程式碼會需要與原生結構之資料配置對等的 Managed 結構。  不過，包含指標的結構還需要特別處理。  對於每個原生結構中的內嵌指標，結構的 Managed 版本應該包含 <xref:System.IntPtr> 型別的執行個體。  此外，這些執行個體的記憶體必須使用 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>、<xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A> 和 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> 方法，明確地配置、初始化和釋放。  
  
 下列程式碼由 Unmanaged 和 Managed 的模組所組成。  Unmanaged 模組是 DLL，它會定義接受名稱為 ListString 結構 \(結構中包含指標\) 的函式，以及名稱為 TakesListStruct 的函式。  Managed 模組是命令列應用程式，它會匯入 TakesListStruct 函式並定義名稱為 MListStruct 的結構，此結構與原生的 ListStruct 對等，除了 double\* 以 <xref:System.IntPtr> 執行個體表示以外。  在呼叫 TakesListStruct 之前，main 函式會配置並初始化這個欄位參考的記憶體。  
  
 Managed 模組是使用 \/clr 編譯的，但是 \/clr:pure 也一樣可以執行。  
  
```  
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
  
```  
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
  
 請注意，DLL 的任何部分不會都公開給使用傳統 \#include 指示詞的 Managed 程式碼。  事實上，DLL 只會在執行階段存取，所以使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 匯入之函式所產生的問題，不會在編譯時期偵測出來。  
  
## 請參閱  
 [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)