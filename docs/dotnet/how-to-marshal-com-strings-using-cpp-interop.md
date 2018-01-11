---
title: "如何： 使用 c + + Interop 封送處理 COM 字串 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 45a79f3aa78d229c71aba5a1d1144d05afe7bbd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>如何：使用 C++ Interop 封送處理 COM 字串
本主題會示範如何 BSTR （偏好在 COM 程式設計中的基本字串格式） 傳遞從 managed 到 unmanaged 函式，反之亦然。 與其他字串類型間的互通性，請參閱下列主題：  
  
-   [如何：使用 C++ Interop 封送處理 Unicode 字串](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [如何：使用 C++ Interop 封送處理 ANSI 字串](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 下列程式碼範例使用[managed、 unmanaged](../preprocessor/managed-unmanaged.md) #pragma 指示詞來實作 managed 和 unmanaged 函式在相同的檔案，但如果在不同的檔案中定義這些函式交互操作的方式相同。 檔案，其中包含只在 unmanaged 函式不需要進行編譯[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何將傳遞 BSTR （在 COM 程式設計中使用字串格式） 從 managed 到 unmanaged 函式。 呼叫 managed 函式會使用<xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A>取得內容的.NET System.String BSTR 表示的位址。 此指標固定使用[pin_ptr (C + + /CLI)](../windows/pin-ptr-cpp-cli.md)以確保其實體位址為不變更在記憶體回收循環期間 unmanaged 函式執行時。 記憶體回收行程禁止移動記憶體中的，直到[pin_ptr (C + + /CLI)](../windows/pin-ptr-cpp-cli.md)超出範圍。  
  
```  
// MarshalBSTR1.cpp  
// compile with: /clr  
#define WINVER 0x0502  
#define _AFXDLL  
#include <afxwin.h>  
  
#include <iostream>  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(BSTR bstr) {  
   printf_s("%S", bstr);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = "test string";  
  
   IntPtr ip = Marshal::StringToBSTR(s);  
   BSTR bs = static_cast<BSTR>(ip.ToPointer());  
   pin_ptr<BSTR> b = &bs;  
  
   NativeTakesAString( bs );  
   Marshal::FreeBSTR(ip);  
}  
```  
  
## <a name="example"></a>範例  
 下列範例會示範如何將傳遞 BSTR 從 unmanaged 至 unmanaged 的函式。 接收 managed 函式可以使用中的字串為 BSTR 或<xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A>將它轉換為<xref:System.String>用於與其他 managed 函式。 Unmanaged 堆積上配置記憶體表示 BSTR，因為沒有釘選是有必要，因為沒有未受管理的堆積上沒有記憶體回收。  
  
```  
// MarshalBSTR2.cpp  
// compile with: /clr  
#define WINVER 0x0502  
#define _AFXDLL  
#include <afxwin.h>  
  
#include <iostream>  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedTakesAString(BSTR bstr) {  
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));  
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);  
}  
  
#pragma unmanaged  
  
void UnManagedFunc() {  
   BSTR bs = SysAllocString(L"test string");  
   printf_s("(unmanaged) passing BSTR to managed func...\n");  
   ManagedTakesAString(bs);  
}  
  
#pragma managed  
  
int main() {  
   UnManagedFunc();  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)