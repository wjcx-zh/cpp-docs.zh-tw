---
title: "呼叫原生函式，從 Managed 程式碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 159b80fcc015db2999309fe99e9617f7dcd409ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="calling-native-functions-from-managed-code"></a>從 Managed 程式碼呼叫原生函式
Common language runtime 提供的平台叫用服務或 PInvoke，可讓 managed 程式碼能夠呼叫 C 樣式函式在原生動態連結程式庫 (Dll)。 相同的資料封送處理會用於執行階段和 「 它只著作 」 或 IJW、 機制的 COM 互通性。  
  
 如需詳細資訊，請參閱:  
  
-   [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [詳述平台叫用](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 本節中的範例只說明如何`PInvoke`可用。 `PInvoke`可簡化自訂的資料封送處理，因為您提供宣告式屬性，而不是寫入程序封送處理程式碼封送處理資訊。  
  
> [!NOTE]
>  封送處理程式庫提供原生和 managed 環境，以最佳化方式之間的資料封送處理的替代方式。 請參閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)如需有關封送處理程式庫。 函式僅資料，而不使用封送處理程式庫。  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 DllImport 屬性  
 下列範例示範使用`PInvoke`Visual c + + 程式中。 原生函式將會定義在 msvcrt.dll。 DllImport 屬性用於將的宣告。  
  
```  
// platform_invocation_services.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[DllImport("msvcrt", CharSet=CharSet::Ansi)]  
extern "C" int puts(String ^);  
  
int main() {  
   String ^ pStr = "Hello World!";  
   puts(pStr);  
}  
```  
  
 下列範例就相當於先前範例中，但使用 IJW。  
  
```  
// platform_invocation_services_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#include <stdio.h>  
  
int main() {  
   String ^ pStr = "Hello World!";  
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();   
   puts(pChars);  
  
   Marshal::FreeHGlobal((IntPtr)pChars);  
}  
```  
  
### <a name="advantages-of-ijw"></a>IJW 的優點  
  
-   不需要撰寫`DLLImport`屬性程式會使用的 unmanaged api 的宣告。 只包含標頭檔和匯入程式庫的連結。  
  
-   IJW 機制會稍微快一點 （例如，IJW 虛設常式不需要檢查需要 pin 碼或複製資料的項目，因為該作業由開發人員明確執行）。  
  
-   它會清楚地說明效能問題。 在此情況下，從 Unicode 字串為 ANSI 字串，以及您要將轉譯的事實有附帶的記憶體配置和解除配置。 在此情況下，開發人員撰寫使用 IJW 的程式碼會了解呼叫`_putws`和使用`PtrToStringChars`會是較佳的效能。  
  
-   如果您呼叫許多 unmanaged 應用程式開發介面使用相同的資料封送處理一次，並傳遞的封送處理的複本是比重新封送處理每次更有效率。  
  
### <a name="disadvantages-of-ijw"></a>IJW 的缺點  
  
-   封送處理必須明確指定在程式碼，而不是由屬性 （它們通常有適當的預設值）。  
  
-   封送處理程式碼是內嵌，是在應用程式邏輯的流程較具侵入性。  
  
-   因為明確封送處理 Api 傳回`IntPtr`32 位元到 64 位元可攜性的類型，您必須使用額外`ToPointer`呼叫。  
  
 C + + 所公開的特定方法是更有效率、 明確的方法，但要付出一些額外的複雜性。  
  
 如果應用程式會使用主要是將 unmanaged 的資料類型，或如果呼叫 unmanaged 的 Api 更比.NET Framework Api，我們建議您將使用 IJW 功能。 若要呼叫偶爾 unmanaged 的 API 的大部分受管理的應用程式中，選擇並更難捉摸。  
  
## <a name="pinvoke-with-windows-apis"></a>使用 Windows Api 的 PInvoke  
 PInvoke 是方便您在 Windows 中呼叫函式。  
  
 在此範例中，Visual c + + 程式是 Win32 API 的一部分的 MessageBox 函式與相互操作。  
  
```  
// platform_invocation_services_4.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
typedef void* HWND;  
[DllImport("user32", CharSet=CharSet::Ansi)]  
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);  
  
int main() {  
   String ^ pText = "Hello World! ";  
   String ^ pCaption = "PInvoke Test";  
   MessageBox(0, pText, pCaption, 0);  
}  
```  
  
 輸出是訊息方塊標題 PInvoke 測試，且包含文字 Hello World ！。  
  
 封送處理資訊也可由 PInvoke 來查閱在 DLL 中函式。 User32.dll 中沒有事實上沒有 MessageBox 函式，但 CharSet = CharSet::Ansi 啟用使用 MessageBoxA，ANSI 版本中，而不是 MessageBoxW，也就是 Unicode 版本的 PInvoke。 一般情況下，我們建議您使用的 unmanaged Api 的 Unicode 版本，因為可消除負擔從原生 Unicode 格式的轉譯.NET Framework 的 string 物件為 ANSI。  
  
## <a name="when-not-to-use-pinvoke"></a>不使用 PInvoke 時機  
 使用 PInvoke 不適當的 Dll 中的所有 C 樣式函式。 例如，假設那里中 mylib.dll MakeSpecial 函式宣告，如下所示：  
  
 `char * MakeSpecial(char * pszString);`  
  
 如果我們使用 PInvoke Visual c + + 應用程式中，我們可以撰寫類似下面的內容：  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 困難在於是我們無法刪除 MakeSpecial 所傳回的 unmanaged 字串的記憶體。 透過 PInvoke 呼叫其他函式傳回不需要由使用者取消配置的內部緩衝區的指標。 在此情況下，使用 IJW 功能是顯而易見的選項。  
  
## <a name="limitations-of-pinvoke"></a>PInvoke 的限制  
 您無法從先前做為參數的原生函式傳回完全相同的指標。 如果原生函式會傳回已封送處理的指標，由 PInvoke，可能會發生記憶體損毀和例外狀況。  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 下列範例會顯示這個問題，並輸出即使程式來提供正確的輸出看起來，來自已經釋放的記憶體。  
  
```  
// platform_invocation_services_5.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
#include <limits.h>  
  
ref struct MyPInvokeWrap {  
public:  
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]  
   static String^ CharLower([In, Out] String ^);  
};  
  
int main() {  
   String ^ strout = "AabCc";  
   Console::WriteLine(strout);  
   strout = MyPInvokeWrap::CharLower(strout);  
   Console::WriteLine(strout);  
}  
```  
  
## <a name="marshaling-arguments"></a>封送處理引數  
 與`PInvoke`，沒有封送處理需要之間 managed 和 c + + 原生基本型別使用相同的格式。 例如，沒有封送處理是需要 Int32 和 int 或 Double 及雙間。  
  
 不過，您必須封送處理不會有相同的形式的類型。 這包括字元、 字串和結構類型。 下表顯示各種類型的封送處理器所使用的對應：  
  
|wtypes.h|Visual C++|以 /clr visual c + +|Common Language Runtime|  
|--------------|------------------|-----------------------------|-----------------------------|  
|HANDLE|void *|void *|IntPtr、 UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|SHORT|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|LONG|long|long|Int32|  
|BOOL|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|char *|字串 ^ [in]，StringBuilder ^ [中，out]|字串 ^ [in]，StringBuilder ^ [中，out]|  
|LPCSTR|const char *|字串 ^|String|  
|LPWSTR|wchar_t *|字串 ^ [in]，StringBuilder ^ [中，out]|字串 ^ [in]，StringBuilder ^ [中，out]|  
|LPCWSTR|const wchar_t *|字串 ^|String|  
|FLOAT|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 封送處理器會自動釘選如果其位址傳遞至 unmanaged 函式，在執行階段堆積上配置記憶體。 Pin 可防止記憶體回收行程移動壓縮時的記憶體配置的區塊。  
  
 在本主題稍早所示的範例中，DllImport CharSet 參數會指定如何 managed 的字串應該封送處理。在此情況下，它們應該封送處理為原生的側邊的 ANSI 字串。  
  
 您可以使用 MarshalAs 屬性，以指定原生函式的各個引數封送處理的資訊。 有幾個選擇可封送處理字串 * 引數： BStr、 ansibstr 的功能、 TBStr、 LPStr、 LPWStr 和 LPTStr。 預設為 LPStr。  
  
 在此範例中，字串會以雙位元組 Unicode 字元字串，LPWStr 封送處理。 輸出會是第一個字母的 Hello World ！ 因為封送處理字串的第二個位元組是 null，而且將解譯為字串結尾標記。  
  
```  
// platform_invocation_services_3.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[DllImport("msvcrt", EntryPoint="puts")]  
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);  
  
int main() {  
   String ^ pStr = "Hello World!";  
   puts(pStr);  
}  
```  
  
 MarshalAs 屬性是 System::Runtime::InteropServices 命名空間中。 屬性可以搭配其他資料類型，例如陣列。  
  
 如稍早在本主題中所述，封送處理程式庫會提供新且最佳化的原生和 managed 環境之間的資料封送處理方法。 如需詳細資訊，請參閱[概觀的封送處理 c + + 中](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
## <a name="performance-considerations"></a>效能考量  
 PInvoke 具有介於 10 到 30 之間的額外負荷 x86 指示每個呼叫。 這個固定成本，除了封送處理會建立額外負擔。 Blittable 類型在 managed 和 unmanaged 程式碼中具有相同的表示法之間沒有任何封送處理的成本。 比方說，是轉譯 int 與 Int32 之間沒有成本。  
  
 為提升效能，有較少越好，而不是封送處理較少的資料，每個呼叫的多個呼叫，最多資料封送處理的 PInvoke 呼叫。  
  
## <a name="see-also"></a>請參閱  
 [原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)