---
title: C + + 中封送處理概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 60706a7922d9bea68e2ef4a27afa1401a1cd6920
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377444"
---
# <a name="overview-of-marshaling-in-c"></a>C++ 中封送處理的概觀

在混合模式中，您有時必須封送處理原生和 managed 型別之間資料。 Visual Studio 2008 中引進*封送處理程式庫*為了封送處理，並將資料轉換的簡單方式。  封送處理程式庫包含一組函式和`marshal_context`執行封送處理的常見類型的類別。 在這些標頭中所定義的程式庫**msclr 包含**目錄，您的 Visual Studio 版本：

|頁首|描述|
|---------------|-----------------|
|marshal.h|`marshal_context` 類別和內容免費封送處理函式|
|marshal_atl.h| ATL 類型封送處理函式|
|marshal_cppstd.h|標準 c + + 類型封送處理函式|
|marshal_windows.h|Windows 類型封送處理函式|

預設路徑**msclr**資料夾是類似下面的版本視您擁有和組建編號：

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

您可以使用封送處理程式庫，包含或不含[marshal_context 類別](../dotnet/marshal-context-class.md)。 某些轉換需要內容。 其他轉換可以使用來實作[marshal_as](../dotnet/marshal-as.md)函式。 下表列出目前支援的轉換、 是否需要的內容，以及哪些封送處理檔案，您必須包含：

|從型別|若要輸入|封送處理方法|包含檔案|
|---------------|-------------|--------------------|------------------|
|System:: string ^|const char \*|marshal_context|marshal.h|
|const char \*|System:: string ^|marshal_as|marshal.h|
|Char \*|System:: string ^|marshal_as|marshal.h|
|System:: string ^|const wchar_t\*|marshal_context|marshal.h|
|const wchar_t \*|System:: string ^|marshal_as|marshal.h|
|wchar_t \*|System:: string ^|marshal_as|marshal.h|
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|
|System:: string ^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System:: string ^|marshal_as|marshal.h|
|System:: string ^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System:: string ^|marshal_as|marshal_windows.h|
|System:: string ^|std:: string|marshal_as|marshal_cppstd.h|
|std:: string|System:: string ^|marshal_as|marshal_cppstd.h|
|System:: string ^|std:: wstring|marshal_as|marshal_cppstd.h|
|std:: wstring|System:: string ^|marshal_as|marshal_cppstd.h|
|System:: string ^|CStringT\<char >|marshal_as|marshal_atl.h|
|CStringT\<char >|System:: string ^|marshal_as|marshal_atl.h|
|System:: string ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|
|CStringT < wchar_t >|System:: string ^|marshal_as|marshal_atl.h|
|System:: string ^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System:: string ^|marshal_as|marshal_atl.h|

只有在您封送處理為原生受管理的資料類型，並清除您要將它轉換成原生型別沒有自動的解構函式時，封送處理需要內容。 封送處理的內容會終結其解構函式中的已配置的原生資料類型。 因此，需要內容的轉換是有效的內容會被刪除時，才。 若要儲存任何封送處理的值，您必須將值複製到自己的變數。

> [!NOTE]
>  如果您已嵌入`NULL`在字串中的 s，不保證封送處理字串的結果。 內嵌`NULL`s 可能會導致要截斷的字串，或可能會保留。

此範例示範如何在包含標頭宣告包含 msclr 目錄：

`#include "msclr\marshal_cppstd.h"`

封送處理程式庫是可延伸，以便您可以新增您自己的封送處理類型。 如需有關擴充封送處理程式庫的詳細資訊，請參閱[如何： 擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)。

在舊版中，您無法封送處理資料使用[平台叫用](/dotnet/framework/interop/consuming-unmanaged-dll-functions)。 如需詳細資訊`PInvoke`，請參閱 <<c2> [ 從 Managed 程式碼呼叫原生函數](../dotnet/calling-native-functions-from-managed-code.md)。

## <a name="see-also"></a>另請參閱

[C++ 支援程式庫](../dotnet/cpp-support-library.md)<br/>
[如何：擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)
