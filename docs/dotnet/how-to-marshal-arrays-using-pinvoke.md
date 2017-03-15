---
title: "如何：使用 PInvoke 封送處理陣列 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料封送處理 [C++], 陣列"
  - "Interop [C++], 陣列"
  - "封送處理 [C++], 陣列"
  - "平台叫用 [C++], 陣列"
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：使用 PInvoke 封送處理陣列
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會說明如何使用 .NET Framework Platform Invoke 支援，以 CLR 字串型別 <xref:System.String> 呼叫接受 C\-Style 字串的原生 \(Native\) 函式。  我們鼓勵 Visual C\+\+ 程式設計人員盡可能改用 C\+\+ Interop 功能，因為 P\/Invoke 提供極少的編譯時期錯誤報告，不具型別安全，而且實作時很瑣碎無聊。  如果 Unmanaged API 封裝為 DLL，而且沒有原始程式碼，則 P\/Invoke 是唯一的選擇 \(否則請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)\)。  
  
## 範例  
 因為原生和 Managed 陣列在記憶體中排列的方式不同，會需要轉換或封送處理 \(Marshaling\) 以便在 Managed\/Unmanaged 界限之間成功地傳遞這些物件。  本主題會示範如何從 Managed 程式碼將具有簡單 \(blitable\) 項目的陣列傳遞至原生函式。  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性 \(Attribute\) 會用來為每個所用到的原生函式建立 Managed 進入點 \(對於 Managed\/Unmanaged 資料封送處理而言通常是如此\)。  對於取用陣列作為引數的函式，必須使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性並且對編譯器 \(Compiler\) 指定資料封送處理的方式。  在下列範例中，<xref:System.Runtime.InteropServices.UnmanagedType> 列舉型別會用來表示 Managed 陣列將會封送處理成 C\-Style 陣列。  
  
 下列程式碼由 Unmanaged 和 Managed 的模組所組成。  Unmanaged 模組是 DLL，定義接受整數陣列的函式。  第二個模組是匯入這個函式的 Managed 命令列應用程式，但是使用 Managed 陣列定義此函式，並使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性，指定呼叫時要將陣列轉換為原生陣列。  
  
 Managed 模組是使用 \/clr 編譯的，但是 \/clr:pure 也一樣可以執行。  
  
```  
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
  
```  
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
  
 請注意，傳統 \#include 指示詞不會將 DLL 的任何部分公開 \(Expose\) 給 Managed 程式碼。  事實上，因為只會在執行階段存取 DLL，使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 匯入之函式所產生的問題，就不會在編譯時期偵測出來。  
  
## 請參閱  
 [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)