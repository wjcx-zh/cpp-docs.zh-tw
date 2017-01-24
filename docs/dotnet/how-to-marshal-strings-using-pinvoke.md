---
title: "如何：使用 PInvoke 封送處理字串 | Microsoft Docs"
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
  - "資料封送處理 [C++], 字串"
  - "Interop [C++], 字串"
  - "封送處理 [C++], 字串"
  - "平台叫用 [C++], 字串"
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 PInvoke 封送處理字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題會說明如何使用 .NET Framework Platform Invoke 支援，以 CLR 字串型別 System::String 呼叫接受 C\-Style 字串的原生 \(Native\) 函式。  我們鼓勵 Visual C\+\+ 程式設計人員盡可能改用 C\+\+ Interop 功能，因為 P\/Invoke 提供極少的編譯時期錯誤報告，不具型別安全，而且實作時很瑣碎無聊。  如果 Unmanaged API 封裝為 DLL，而且沒有原始程式碼，則 P\/Invoke 是唯一的選擇，但是若非如此則請參閱[使用 C\+\+ Interop \(隱含 PInvoke\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 Managed 和 Unmanaged 字串在記憶體中排列的方式不同，所以從 Managed 函式將字串傳遞至 Unmanaged 函式會需要 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性 \(Attribute\) 以指示編譯器 \(Compiler\) 插入必要的轉換機制，以正確且安全地封送處理 \(Marshaling\) 字串資料。  
  
 至於只使用內建資料型別的函式，<xref:System.Runtime.InteropServices.DllImportAttribute> 會用來宣告對原生函式的 Managed 進入點，但是對傳遞字串而言，不一定要將這些進入點定義為取用 C\-Style 字串，您可以改用 <xref:System.String> 型別的控制代碼。  這會提示編譯器插入可執行必要轉換的程式碼。  對於取用字串的 Unmanaged 函式中的每個函式引數，應該要使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性以表示 String 物件要封送處理為 C\-Style 字串並傳遞至原生函式。  
  
## 範例  
 下列程式碼由 Unmanaged 和 Managed 模組所組成。  Unmanaged 模組是 DLL，定義名稱為 TakesAString 的函式，且此函式接受 char\* 形式的 C\-Style ANSI 字串。  Managed 模組是匯入 TakesAString 函式的命令列應用程式，但是會將函式定義為取用 Managed System.String 而不是 char\*。  <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性用來表示在呼叫 TakesAString 時要如何封送處理 Managed 字串。  
  
 Managed 模組是使用 \/clr 編譯的，但是 \/clr:pure 也一樣可以執行。  
  
```  
// TraditionalDll2.cpp  
// compile with: /LD /EHsc  
#include <windows.h>  
#include <stdio.h>  
#include <iostream>  
  
using namespace std;  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAString(char*);  
}  
  
void TakesAString(char* p) {  
   printf_s("[unmanaged] %s\n", p);  
}  
```  
  
```  
// MarshalString.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL  
{  
   [DllImport("TraditionalDLL2.dll")]  
      static public void   
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);  
};  
  
int main() {  
   String^ s = gcnew String("sample string");  
    Console::WriteLine("[managed] passing managed string to unmanaged function...");  
   TraditionalDLL::TakesAString(s);  
   Console::WriteLine("[managed] {0}", s);  
}  
```  
  
 這項技術會在 Unmanaged 堆積 \(Heap\) 上建構字串的複本，所以原生函式對字串所做的變更不會反映至字串的 Managed 複本。  
  
 請注意，DLL 的任何部分都不會經由傳統 \#include 指示詞公開 \(Expose\) 給 Managed 程式碼。  事實上，只會在執行階段存取 DLL，所以使用 `DllImport` 匯入之函式所產生的問題，不會在編譯時期偵測出來。  
  
## 請參閱  
 [在 C\+\+ 中使用明確的 PInvoke \(DllImport 屬性\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)