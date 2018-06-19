---
title: 如何： 使用 PInvoke 封送處理字串 |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1a377e7074e72693a1a63e392c64a6d60c5995b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133203"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>如何：使用 PInvoke 封送處理字串
本主題說明如何原生函式接受 C 樣式字串可以呼叫使用 CLR 字串類型使用.NET Framework 平台叫用支援的 system:: string。 Visual c + + 程式設計人員會建議 （自動），而是使用 c + + Interop 功能，因為 P/Invoke 提供極少的編譯時間錯誤報告，不是類型安全，就必須等待冗長實作。 如果未受管理的應用程式開發介面會封裝為 DLL，且不提供原始程式碼，P/Invoke 是唯一的選項，但否則看到[使用 c + + Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
 Managed 和 unmanaged 字串以不同的方式在配置記憶體，因此傳遞字串從 managed 到 unmanaged 函式需要<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性指示編譯器插入封送處理字串資料的必要的轉換機制正確且安全地。  
  
 如同使用只有內建資料類型的函式<xref:System.Runtime.InteropServices.DllImportAttribute>用來宣告 managed 的進入點到原生函式中，-但傳遞字串-而不是定義為接受 C 樣式字串的控制代碼的這些項目點<xref:System.String>類型可以改為使用。 這會提示編譯器插入程式碼會執行必要的轉換。 每個函式引數在 unmanaged 函式可接受 string，<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性應該用來表示的字串物件，應該封送處理為 C 樣式字串原生函式。  
  
## <a name="example"></a>範例  
 下列程式碼是由 unmanaged 和 managed 的模組所組成。 未受管理的模組是定義函式，呼叫可接受 ANSI C 樣式字串形式的 char * TakesAString 的 DLL。 受管理的模組是命令列應用程式匯入 TakesAString 函式，但定義為受管理的 System.String，而不是 char\*。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性用來指示如何的 managed 的字串應該封送處理呼叫 TakesAString 時。  
  
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
  
 這項技術會導致要建構 unmanaged 堆積上，所以字串對原生函式所做的變更不會反映在字串的受管理的複本中字串的複本。  
  
 請注意 DLL 的任何部分公開給 managed 程式碼，透過傳統 #include 指示詞。 事實上，DLL 會存取在執行階段，因此問題函式匯入與`DllImport`將不會在編譯時期偵測。  
  
## <a name="see-also"></a>另請參閱  
 [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)