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
ms.openlocfilehash: 285bfabbd5935df303a39ada11c388713ae24f34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209187"
---
# <a name="calling-native-functions-from-managed-code"></a>從 Managed 程式碼呼叫原生函式

Common language runtime 提供平台叫用服務或 PInvoke，可讓 managed 程式碼呼叫原生動態連結程式庫 (Dll) 中的 C 樣式函式。 相同封送處理的資料會用於 COM 互通性與執行階段以及"It Just Works"（IJW) 機制。

如需詳細資訊，請參閱:

- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

此章節中的範例僅說明如何`PInvoke`可用。 `PInvoke` 可以簡化自訂的資料封送處理，因為您提供封送處理資訊而非撰寫程序的封送處理程式碼的屬性中以宣告方式。

> [!NOTE]
>  封送處理的程式庫會提供資料以最佳化方式的原生和 managed 環境之間封送處理的替代方式。 請參閱[Overview of Marshaling 中C++](../dotnet/overview-of-marshaling-in-cpp.md)如需有關封送處理程式庫。 封送處理程式庫是使用僅限資料，而非用於函式。

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 和 DllImport 屬性

下列範例示範使用`PInvoke`視覺效果中C++程式。 原生函式 puts 定義於 msvcrt.dll。 DllImport 屬性用於宣告 puts。

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

下列範例相當於先前的範例中，但使用 IJW。

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

- 不需要撰寫`DLLImport`屬性宣告的程式使用的 unmanaged api。 只包含標頭檔和匯入程式庫的連結。

- IJW 機制會稍微快 （例如，IJW stub 不需要檢查是否要固定或複製資料項目，因為該作業由開發人員明確執行）。

- 它清楚說明效能問題。 在此情況下，會從 Unicode 字串轉譯成 ANSI 字串，而且您的事實會有附帶的記憶體配置和解除配置。 在此情況下，開發人員撰寫程式碼使用 IJW 會了解，呼叫`_putws`並使用`PtrToStringChars`會得到較佳的效能。

- 如果您呼叫許多 unmanaged 的 Api 使用相同的資料封送處理它一次，並傳遞封送處理的複製就會是比重新封送處理每次更有效率。

### <a name="disadvantages-of-ijw"></a>IJW 的缺點

- 封送處理必須明確指定在程式碼，而不是由屬性 （這通常會有適當的預設值）。

- 封送處理程式碼是以內嵌，其所在的應用程式邏輯流程中較具侵入性。

- 由於明確封送處理 Api 會傳回`IntPtr`32 位元到 64 位元可攜性的類型，您必須使用額外`ToPointer`呼叫。

所公開的特定方法C++是更有效率且明確的方法，但代價是額外的複雜度。

如果應用程式會使用主要 unmanaged 的資料類型，或如果它呼叫 unmanaged 的 Api 多於.NET Framework Api 時，我們建議您將使用 IJW 功能。 若要在多半為 managed 應用程式中呼叫偶爾 unmanaged 的 API，選擇是更為合適。

## <a name="pinvoke-with-windows-apis"></a>PInvoke 與 Windows Api

PInvoke 是方便您在 Windows 中呼叫函式。

在此範例中，視覺效果C++程式交互操作的 MessageBox 函式，是 Win32 API 的一部分。

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

輸出是訊息方塊具有標題為 PInvoke Test 且包含文字 Hello World ！。

PInvoke 也會使用封送處理的資訊來查詢 DLL 中的函式。 在 user32.dll 中沒有其實沒有 MessageBox 函式，但 CharSet = charset:: Ansi 允許 PInvoke 使用 MessageBoxA，ANSI 版本，而不是 MessageBoxW，也就是 Unicode 版本。 一般情況下，我們建議您使用的 unmanaged Api 的 Unicode 版本，因為這樣會免除從原生 Unicode 格式的額外負荷的轉譯.NET Framework 的 string 物件為 ANSI。

## <a name="when-not-to-use-pinvoke"></a>不使用 PInvoke 的時機

使用 PInvoke 不適用於 Dll 中的所有 c-style 函式。 例如，假設那里 mylib.dll 中的函式 MakeSpecial 宣告，如下所示：

`char * MakeSpecial(char * pszString);`

如果我們使用視覺效果中的 PInvokeC++應用程式中，我們可能會撰寫類似下列內容：

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

困難之處在於，我們無法刪除 MakeSpecial 所傳回之 unmanaged 字串的記憶體。 其他透過 PInvoke 所呼叫的函式會傳回不需要由使用者解除配置的內部緩衝區的指標。 在此情況下，使用 IJW 功能是理所當然的選擇。

## <a name="limitations-of-pinvoke"></a>PInvoke 的限制

您無法從先前做為參數的原生函式來傳回完全相同的指標。 如果原生函式會傳回它被封送處理的指標，由 PInvoke，可能會發生記憶體損毀和例外狀況。

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

下列範例會顯示這個問題，並輸出即使程式看起來提供正確的輸出，來自已經釋放的記憶體。

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

具有`PInvoke`，沒有封送處理之間需要管理和C++具有相同格式的原生基本類型。 例如，沒有封送處理是必要 Int32 與 int 之間，或 Double 與 double 之間。

不過，您必須封送處理類型，並沒有相同的格式。 這包括 char、 string 和 struct 類型。 下表顯示各種類型封送處理器所使用的對應：

|wtypes.h|Visual C++|視覺化C++以 /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|Void \*|Void \*|IntPtr、 UIntPtr|
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
|LPCSTR|Char \*|字串 ^ [in]，StringBuilder ^ [在中，out]|字串 ^ [in]，StringBuilder ^ [在中，out]|
|LPCSTR|const char \*|字串 ^|String|
|LPWSTR|wchar_t \*|字串 ^ [in]，StringBuilder ^ [在中，out]|字串 ^ [in]，StringBuilder ^ [在中，out]|
|LPCWSTR|const wchar_t \*|字串 ^|String|
|FLOAT|float|float|Single|
|DOUBLE|double|double|Double|

封送處理器會自動釘選它的位址傳遞至 unmanaged 函式在執行階段堆積上配置的記憶體。 釘選可防止記憶體回收行程在壓縮期間移動的記憶體配置的區塊。

在本主題稍早所示的範例中，DllImport 的 CharSet 參數指定了解受管理的字串應該封送處理;在此情況下，它們應封送處理原生端的 ANSI 字串。

您可以使用 MarshalAs 屬性指定原生函式個別引數封送處理的資訊。 有數種選擇來封送處理字串\*引數：BStr、 ANSIBStr、 TBStr、 LPStr、 LPWStr 和 LPTStr。 預設值為 LPStr。

在此範例中，字串會封送處理為雙位元組 Unicode 字元字串 LPWStr。 輸出是 Hello World 的第一個字母 ！ 因為封送處理字串的第二個位元組是 null，而且 puts 會將此視為字串結尾標記。

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

MarshalAs 屬性位於 System::Runtime::InteropServices 命名空間。 屬性可以搭配其他資料類型，例如陣列。

如本主題稍早所述，封送處理程式庫會提供全新最佳化方法的封送處理原生和 managed 環境之間的資料。 如需詳細資訊，請參閱 < [Overview of Marshaling 中C++ ](../dotnet/overview-of-marshaling-in-cpp.md)。

## <a name="performance-considerations"></a>效能考量

PInvoke 的額外負荷介於 10 到 30 之間 x86 每次呼叫的指示。 除了這個固定成本，封送處理會建立額外負荷。 在 managed 和 unmanaged 程式碼中有相同表示的 blittable 類型之間沒有任何封送處理的成本。 比方說，是 int 和 Int32 之間轉譯任何成本。

為了達到最佳效能，有較少越好，而不是封送處理較少的資料，每次呼叫的多個呼叫，最多資料封送處理的 PInvoke 呼叫。

## <a name="see-also"></a>另請參閱

[原生和 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)
