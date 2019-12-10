---
title: 從 Managed 程式碼呼叫原生函式
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 50f40cc147daaa26a7fa4e607f0d4dd42cf22d61
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988663"
---
# <a name="calling-native-functions-from-managed-code"></a>從 Managed 程式碼呼叫原生函式

Common Language Runtime 提供了平台引動服務 (Platform Invocation Services，PInvoke)，可讓 Managed 程式碼呼叫原生動態連結程式庫 (DLL) 中的 C-Style 函式。 所使用的資料封送處理，與 COM 和執行階段的互通性以及 "It Just Works" (IJW) 機制所使用的相同。

如需詳細資訊，請參閱＜＞。

- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

本章節中的範例僅說明如何使用 `PInvoke`。 因為您會在屬性 (Attribute) 中以宣告方式提供封送處理資訊，而非撰寫程序性封送處理程式碼，因此 `PInvoke` 可以簡化自訂的資料封送處理。

> [!NOTE]
>  封送處理程式庫所提供的替代方式，能夠以最佳化的方式在原生及 Managed 環境之間封送處理資料。 如需封送處理程式庫的詳細資訊，請參閱[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。 封送處理程式庫僅供資料使用，而不能由函式使用。

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 DllImport 屬性

下列範例會示範在 Visual C++ 程式中使用 `PInvoke`。 原生函式 puts 定義於 msvcrt.dll。 DllImport 屬性會用來宣告 puts。

```cpp
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

下列範例的作用與上一個範例相同，但使用 IJW。

```cpp
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

- 不需為程式所使用的 Unmanaged API 撰寫 `DLLImport` 屬性宣告。 只要包含標頭檔和並與匯入程式庫連結即可。

- IJW 機制會更快一點 (例如，IJW Stub 不需要檢查是否要固定或複製資料項目，因為該作業是由開發人員明確執行)。

- 它清楚說明效能問題。 在這個案例中，事實上您必須從 Unicode 字串轉譯成 ANSI 字串，並有附帶的記憶體配置和解除配置。 使用 IJW 撰寫程式碼的開發人員應該了解，呼叫 `_putws` 並使用 `PtrToStringChars` 會得到較佳效能。

- 如果您使用相同資料來呼叫許多 Unmanaged API，請進行一次封送處理，然後傳遞封送處理過的複本，這樣比起每次重新封送處理會更有效率。

### <a name="disadvantages-of-ijw"></a>IJW 的缺點

- 封送處理必須在程式碼中明確指定，而不是由屬性指定 (通常都會有適當的預設值)。

- 封送處理程式碼是內嵌，在應用程式邏輯流程中較具侵入性。

- 由於明確封送處理 API 會對 32 位元至 64 位元可攜性傳回 `IntPtr` 類型，因此您必須使用額外的 `ToPointer` 呼叫。

C++ 所公開的特定方法是更有效率且明確的方法，但其代價是額外的複雜度。

如果應用程式主要使用 Unmanaged 資料類型，或是呼叫 Unmanaged API 多於 .NET Framework API，我們便會建議您使用 IJW 功能。 若要在多半為 Managed 的應用程式中偶爾呼叫 Unmanaged API，此選擇更為合適。

## <a name="pinvoke-with-windows-apis"></a>PInvoke 與 Windows API

PInvoke 對於呼叫 Windows 中的函式來說非常方便。

在這個範例中，Visual C++ 程式會與 Win32 API 中的 MessageBox 函式互相操作。

```cpp
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

輸出是標題為 PInvoke Test 的訊息方塊，並含有 Hello World! 文字。

PInvoke 也會使用封送處理資訊來查詢 DLL 中的函式。 在 user32.dll 中，其實沒有 MessageBox 函式，但 CharSet=CharSet::Ansi 允許 PInvoke 使用 MessageBoxA (ANSI 版本)，而不是 MessageBoxW (Unicode 版本)。 一般而言，我們建議您使用 Unicode 版本的 Unmanaged API，因為這樣會免除從 .NET Framework 原生 Unicode 格式字串物件轉譯成 ANSI 的額外負荷。

## <a name="when-not-to-use-pinvoke"></a>不使用 PInvoke 的時機

DLL 中的所有 C-Style 函式並不適合使用 PInvoke。 例如，假設在 mylib.dll 中有函式 MakeSpecial 宣告如下：

`char * MakeSpecial(char * pszString);`

如果我們在 Visual C++ 應用程式中使用 PInvoke，可能會撰寫與下列類似的程式碼：

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

其困難之處在於，我們無法刪除 MakeSpecial 所傳回之 Unmanaged 字串的記憶體。 其他透過 PInvoke 所呼叫的函式會傳回內部緩衝區的指標，該緩衝區不需要由使用者解除配置。 在這個案例中，使用 IJW 功能是顯而易見的選項。

## <a name="limitations-of-pinvoke"></a>PInvoke 的限制

從原生函式中，無法傳回先前做為參數的完全相同指標。 如果原生函式傳回已經由 PInvoke 封送處理過的指標，可能會發生記憶體損毀和例外狀況。

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

下列範例中會顯示這個問題，雖然程式看起來提供正確輸出，但輸出其實是來自已經釋放的記憶體。

```cpp
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

使用 `PInvoke` 時，具有相同格式的 Managed 和 C++ 原生基本類型 (Primitive Type) 之間不需要封送處理。 例如，Int32 與 int 之間，或 Double 與 double 之間不需要封送處理。

不過，您必須對沒有相同格式的類型進行封送處理。 這包括 char、string 和 struct 類型。 下表會顯示封送處理器針對各種類型所使用的對應。

|wtypes.h|Visual C++|Visual C++ 含 /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|void \*|void \*|IntPtr、UIntPtr|
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
|LPCSTR|char \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char \*|String ^|String|
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|const wchar_t \*|String ^|String|
|FLOAT|浮動|浮動|Single|
|DOUBLE|雙線|雙線|雙精度浮點數|

如果記憶體位址傳遞至 Unmanaged 函式，封送處理器會自動將記憶體固定在執行階段堆積上。 固定可防止記憶體回收行程在壓縮期間移動記憶體的配置區塊。

在本主題前面的範例中，DllImport 的 CharSet 參數指定 Managed 字串的封送處理方式。在這個案例中，它們應封送處理成原生端的 ANSI 字串。

您可以使用 MarshalAs 屬性指定原生函式個別引數的封送處理資訊。 有數個選項可將字串封送處理 \* 引數： BStr、ANSIBStr、TBStr、LPStr、LPWStr 和 LPTStr。 預設值為 LPStr。

在這個範例中，字串會封送處理成雙位元組 Unicode 字元字串 LPWStr。 輸出是 Hello World 的第一個字母！ 由於封送處理字串的第二個位元組是 null，因此會將它解釋為字串結束記號。

```cpp
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

MarshalAs 屬性位於 System::Runtime::InteropServices 命名空間中。 此屬性可以和其他資料類型 (例如陣列) 一起使用。

如本主題先前所述，封送處理程式庫提供在原生及 Managed 環境之間封送處理資料的全新最佳化方法。 如需詳細資訊，請參閱[中C++的封送處理總覽](../dotnet/overview-of-marshaling-in-cpp.md)。

## <a name="performance-considerations"></a>效能考量

PInvoke 的每呼叫額外負荷介於 10 和 30 x86 個指令之間。 除了這個固定成本，封送處理會產生更多額外負荷。 對於 Managed 和 Unmanaged 程式碼有相同表示的 Blittable 類型間，沒有封送處理成本。 例如，在 int 和 Int32 之間轉譯，沒有任何成本。

如需達成較佳效能，請少量執行封送處理了大量資料的 PInvoke 呼叫，而非大量執行在每次呼叫中封送處理較少資料的呼叫。

## <a name="see-also"></a>請參閱

[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)
