---
title: C++ 中封送處理的概觀
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 937fbdf4b3ed09344e69a8f1eb731565c36794ae
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/12/2019
ms.locfileid: "70311863"
---
# <a name="overview-of-marshaling-in-ccli"></a>/Cli 中C++的封送處理總覽

在混合模式中，您有時必須在原生和 managed 類型之間封送處理您的資料。 *封送處理程式庫*可協助您以簡單的方式封送處理和轉換資料。  封送處理程式庫包含一組函式， `marshal_context`以及針對一般類型執行封送處理的類別。 程式庫定義于您 Visual Studio 版本的**include/msclr**目錄中的這些標頭中：

|標頭|說明|
|---------------|-----------------|
|封送處理。h|`marshal_context`類別和無內容封送處理函式|
|marshal_atl.h| 封送處理 ATL 類型的函式|
|marshal_cppstd.h|封送處理標準C++類型的函數|
|marshal_windows.h|封送處理 Windows 類型的函式|

**Msclr**資料夾的預設路徑與下列內容類別似，視您擁有的版本和組建編號而定：

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

您可以使用包含或不含[Marshal_coNtext 類別](../dotnet/marshal-context-class.md)的封送處理程式庫。 某些轉換需要內容。 您可以使用[marshal_as](../dotnet/marshal-as.md)函數來執行其他轉換。 下表列出目前支援的轉換、是否需要內容，以及您必須包含的封送處理檔案：

|從類型|若要輸入|封送處理方法|Include 檔案|
|---------------|-------------|--------------------|------------------|
|System::String^|const char\*|marshal_context|封送處理。h|
|const char\*|System::String^|marshal_as|封送處理。h|
|char\*|System::String^|marshal_as|封送處理。h|
|System::String^|const wchar_t\*|marshal_context|封送處理。h|
|const wchar_t\*|System::String^|marshal_as|封送處理。h|
|wchar_t\*|System::String^|marshal_as|封送處理。h|
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|
|System::String^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System::String^|marshal_as|封送處理。h|
|System::String^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System::String^|marshal_as|marshal_windows.h|
|System::String^|std：： string|marshal_as|marshal_cppstd.h|
|std：： string|System::String^|marshal_as|marshal_cppstd.h|
|System::String^|std：： wstring|marshal_as|marshal_cppstd.h|
|std：： wstring|System::String^|marshal_as|marshal_cppstd.h|
|System::String^|CStringT\<char>|marshal_as|marshal_atl.h|
|CStringT\<char>|System::String^|marshal_as|marshal_atl.h|
|System::String^|CStringT<wchar_t>|marshal_as|marshal_atl.h|
|CStringT<wchar_t>|System::String^|marshal_as|marshal_atl.h|
|System::String^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System::String^|marshal_as|marshal_atl.h|

只有當您從 managed 封送處理至原生資料類型，而且轉換成的原生類型沒有自動清除的析構函式時，封送處理才需要內容。 封送處理內容會在其析構函式中終結已配置的原生資料類型。 因此，需要內容的轉換只會在內容刪除後才有效。 若要儲存任何封送處理的值，您必須將值複製到您自己的變數。

> [!NOTE]
>  如果您在字串`NULL`中內嵌了，則不保證字串的封送處理結果。 內嵌`NULL`的可能會導致字串截斷或保留。

這個範例示範如何在 include 標頭宣告中包含 msclr 目錄：

`#include "msclr\marshal_cppstd.h"`

封送處理程式庫是可擴充的，因此您可以加入自己的封送處理類型。 如需擴充封送處理程式庫的詳細[資訊，請參閱如何：擴充封送處理](../dotnet/how-to-extend-the-marshaling-library.md)程式庫。

## <a name="see-also"></a>另請參閱

[C++ 支援程式庫](../dotnet/cpp-support-library.md)<br/>
[如何：擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)
