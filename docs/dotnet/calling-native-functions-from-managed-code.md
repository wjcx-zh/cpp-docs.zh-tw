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
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372515"
---
# <a name="calling-native-functions-from-managed-code"></a>從 Managed 程式碼呼叫原生函式

通用語言運行時提供平臺調用服務(PInvoke),使託管代碼能夠在本機動態連結庫(DLL) 中調用 C 樣式函數。 相同的數據封送與 COM 與運行時的互通性以及「它只是工作」或 IJW 機制一樣。

如需詳細資訊，請參閱

- [在 C++ 中使用明確的 PInvoke (DllImport 屬性)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [使用 C++ Interop (隱含 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

目前目前設定的範例僅說明如何`PInvoke`使用 。 `PInvoke`可以簡化自定義的數據封送,因為您在屬性中以聲明性方式提供封送資訊,而不是編寫過程封送代碼。

> [!NOTE]
> 封送庫提供了一種以優化方式在本機環境和託管環境之間封送數據的替代方法。 有關封送庫的詳細資訊,請參閱[C++中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。 封送庫僅可用於數據,不適用於函數。

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke 與 Dll 匯入屬性

下面的範例顯示可檢視C++程式中的使用`PInvoke`。 本機函數放置在 msvcrt.dll 中定義。 DllImport 屬性用於報放。

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

以下示例等效於前面的示例,但使用IJW。

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

### <a name="advantages-of-ijw"></a>IJW 的優勢

- 無需為程式使用的非託管`DLLImport`API 編寫屬性聲明。 只需包括標頭檔和與導入庫的連結。

- IJW 機制稍微快一些(例如,IJW 存根不需要檢查是否需要固定或複製數據項,因為開發人員會顯式執行)。

- 它清楚地說明瞭性能問題。 在這種情況下,您正在從 Unicode 字串轉換為 ANSI 字串,並且具有相應的記憶體分配和處理。 在這種情況下,使用 IJW 編寫代碼的開發人員會意識到`_putws`調用`PtrToStringChars`和使用 將更具有性能。

- 如果使用相同的數據調用許多非託管 API,則將其封送一次並傳遞封送副本比每次重新封送效率高得多。

### <a name="disadvantages-of-ijw"></a>IJW的缺點

- 封送必須在代碼中顯式指定,而不是按屬性(通常具有適當的預設值)指定。

- 封送代碼是內聯的,在應用程式邏輯的流中它更具侵入性。

- 由於顯式封送 API`IntPtr`返回 32 位元到 64 位`ToPointer`元可移植性的類型,因此必須 使用額外的調用。

C++公開的特定方法是更高效、更明確的方法,但代價是一些額外的複雜性。

如果應用程式主要使用非託管數據類型,或者調用比 .NET 框架 API 更多的非託管 API,我們建議您使用 IJW 功能。 要在大多數託管應用程式中調用偶爾的非託管 API,選擇更為微妙。

## <a name="pinvoke-with-windows-apis"></a>使用 Windows API 呼叫

PInvoke 便於在 Windows 中調用函數。

在此示例中,可視化C++程式與作為 Win32 API 一部分的 MessageBox 函數交互。

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

輸出是一個消息框,標題為 PInvoke 測試,並包含文本 Hello World!

PInvoke 還使用封送資訊來查找 DLL 中的函數。 在 user32.dll 中,實際上沒有 MessageBox 函數,但 CharSet_CharSet::Ansi 使 PInvoke 能夠使用消息BoxA(ANSI 版本)而不是 MessageBoxW(即 Unicode 版本)。 通常,我們建議您使用非託管 API 的 Unicode 版本,因為這消除了從 .NET Framework 字串物件的本機 Unicode 格式到 ANSI 的轉換花費。

## <a name="when-not-to-use-pinvoke"></a>何時不使用 PInvoke

使用 PInvoke 不適用於 DLL 中的所有 C 樣式函數。 例如,假設在 mylib.dll 中聲明了一個函數「使特殊」,如下所示:

`char * MakeSpecial(char * pszString);`

如果我們在 Visual C++ 應用程式中使用 PInvoke,我們可能會編寫類似於以下內容的內容:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

這裡的困難是,我們不能刪除 MakeSpecial 返回的非託管字串的記憶體。 通過 PInvoke 調用的其他函數返回指向內部緩衝區的指標,該指標不必由使用者處理。 在這種情況下,使用 IJW 功能是明顯的選擇。

## <a name="limitations-of-pinvoke"></a>PInvoke 的限制

不能從作為參數的本機函數返回完全相同的指標。 如果本機函數返回已由 PInvoke 封送到它的指標,則記憶體損壞和異常可能會隨之而來。

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

下面的示例顯示了此問題,即使程式似乎給出了正確的輸出,輸出來自已釋放的記憶體。

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

## <a name="marshaling-arguments"></a>封送參數

使用`PInvoke`時,在託管和C++具有相同窗體的本機基元類型之間不需要封送。 例如,Int32 和 int 之間或 Double 和 Double 之間不需要封送。

但是,必須對具有相同窗體的類型進行封送。 這包括字元、字串和結構類型。 下表顯示了封送器用於各種類型的對應:

|wtypes.h|Visual C++|帶 /clr 的視覺C++|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|無效\*|無效\*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|SHORT|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|不帶正負號的整數|不帶正負號的整數|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|Boolean|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPSTR|字元\*|字串 = 輸入,字串產生器 = [輸入、出]|字串 = 輸入,字串產生器 = [輸入、出]|
|LPCSTR|康斯特字元\*|字串 ||String|
|LPWSTR|wchar_t \*|字串 = 輸入,字串產生器 = [輸入、出]|字串 = 輸入,字串產生器 = [輸入、出]|
|LPCWSTR|康斯特wchar_t\*|字串 ||String|
|FLOAT|FLOAT|FLOAT|Single|
|DOUBLE|double|double|Double|

如果伺服器的地址傳遞給非託管函數,則封送器會自動將分配給運行時堆的記憶體固定。 固定可防止垃圾回收器在壓縮過程中移動分配的記憶體塊。

在本主題前面所示的示例中,DllImport 的 CharSet 參數指定如何封送託管字串;否則,應如何對託管字串進行封送處理。在這種情況下,它們應被封送到本機端的 ANSI 字串。

可以使用 MarshalAs 屬性為本機函數的各個參數指定封送資訊。 對字串\*參數進行封送有多種選擇:BStr、ANSIBStr、TBStr、LPStr、LPWStr 和 LPTStr。 默認值為 LPStr。

在此範例中,字串作為雙位元組 Unicode 字串 LPWStr 進行封送。 輸出是你好世界的第一個字母! 因為封送字串的第二個字節為空,並且將此解釋為字串結尾標記。

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

MarshalAs 屬性位於系統:運行時::互通服務命名空間。 該屬性可與其他數據類型(如陣列)一起使用。

如本主題前面所述,封送庫提供了一種新的優化數據在本機環境和託管環境之間封送的方法。 有關詳細資訊,請參閱[C++ 中的封送概述](../dotnet/overview-of-marshaling-in-cpp.md)。

## <a name="performance-considerations"></a>效能考量

PInvoke 的開銷介於每個呼叫 10 到 30 x86 指令之間。 除了此固定成本外,封送還會產生額外的開銷。 在託管代碼和非託管代碼中具有相同的表示形式的可聲明類型之間沒有封送成本。 例如,int 和 Int32 之間沒有翻譯費用。

為了更好的性能,減少 PInvoke 調用,以盡可能多地封送數據,而不是使用更多調用來為每個調用封送更少的數據。

## <a name="see-also"></a>另請參閱

[本機與 .NET 互通性](../dotnet/native-and-dotnet-interoperability.md)
