---
title: "如何： 使用 PInvoke 封送處理陣列 |Microsoft 文件"
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
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 50ff0e0a6e61b3c2c691296f92f6ad471a3007e9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>如何：使用 PInvoke 封送處理陣列
本主題說明如何原生函式接受 C 樣式字串可以使用 CLR 字串型別呼叫<xref:System.String>使用.NET Framework 平台叫用支援。 Visual c + + 程式設計人員會建議 （自動），而是使用 c + + Interop 功能，因為 P/Invoke 提供極少的編譯時間錯誤報告，不是類型安全，就必須等待冗長實作。 如果未受管理的應用程式開發介面會封裝為 DLL 不是可用的原始程式碼，P/Invoke 是唯一的選項 (否則請參閱[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md))。  
  
## <a name="example"></a>範例  
 因為原生和 managed 陣列配置以不同的方式在記憶體中，已成功傳遞的 managed/unmanaged 的界限之間需要轉換，或封送處理。 本主題示範如何簡單 (blitable) 項目的陣列可以傳遞至原生函式從 managed 程式碼。  
  
 如為 true 的 managed/unmanaged 資料一般情況下，封送處理的<xref:System.Runtime.InteropServices.DllImportAttribute>屬性用來建立將用於每個原生函式的 managed 的進入點。 在陣列當做引數，不接受函式的情況下<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性必須也用來指定編譯器如何資料會封送處理。 在下列範例中，<xref:System.Runtime.InteropServices.UnmanagedType>列舉型別用來表示，managed 的陣列會封送處理為 C 樣式的陣列。  
  
 下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組會定義接受整數的陣列的函式的 DLL。 第二個模組是受管理的命令列應用程式匯入這個函式，但定義方面的受管理的陣列，並使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性來指定陣列應該將轉換成原生陣列時呼叫。  
  
 以 /clr 編譯 managed 的模組。  
  
```cpp  
// TraditionalDll4.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);  
}  
  
void TakesAnArray(int len, int a[]) {  
   printf_s("[unmanaged]\n");  
   for (int i=0; i<len; i++)  
      printf("%d = %d\n", i, a[i]);  
}  
```  
  
```cpp  
// MarshalBlitArray.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL4.dll")]  
   static public void TakesAnArray(  
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);  
};  
  
int main() {  
   array<int>^ b = gcnew array<int>(3);  
   b[0] = 11;  
   b[1] = 33;  
   b[2] = 55;  
   TraditionalDLL::TakesAnArray(3, b);  
  
   Console::WriteLine("[managed]");  
   for (int i=0; i<3; i++)  
      Console::WriteLine("{0} = {1}", i, b[i]);  
}  
```  
  
 請注意 DLL 的任何部分公開給 managed 程式碼，透過傳統 #include 指示詞。 事實上，因為在執行階段只存取 DLL 時，問題的函式匯入與<xref:System.Runtime.InteropServices.DllImportAttribute>將不會在編譯時期偵測。  
  
## <a name="see-also"></a>請參閱  
 [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)