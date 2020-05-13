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
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372002"
---
# <a name="overview-of-marshaling-in-ccli"></a>C++/CLI 中封送的概述

在混合模式下,有時必須在本機類型和託管類型之間封送數據。 *封送庫*可説明您以簡單方式封送和轉換數據。  封送庫由一組函數和一個`marshal_context`類組成,這些函數和類執行公共類型的封送。 函式庫在 Visual Studio 版的 **「包括/msclr」** 目錄中的這些標頭中定義:

|頁首|描述|
|---------------|-----------------|
|元帥.h|`marshal_context`類別和無上下文封送函數|
|marshal_atl.h| 封送 ATL 類型的函數|
|marshal_cppstd.h|封送標準C++類型的函數|
|marshal_windows.h|封送 Windows 型態的函式|

**msclr**資料夾的預設路徑如下所示,具體取決於您擁有的版本和內部版本號:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

您可以使用帶或不帶[marshal_context 類](../dotnet/marshal-context-class.md)的封送庫。 某些轉換需要上下文。 可以使用[marshal_as](../dotnet/marshal-as.md)函數實現其他轉換。 下表列出了支援的目前轉換、是否需要上下文以及必須包括哪些封送檔:

|從類型|鍵入|封送方法|包括檔案|
|---------------|-------------|--------------------|------------------|
|系統:字串*|康斯特字元\*|marshal_context|元帥.h|
|康斯特字元\*|系統:字串*|marshal_as|元帥.h|
|字元\*|系統:字串*|marshal_as|元帥.h|
|系統:字串*|康斯特wchar_t\*|marshal_context|元帥.h|
|康斯特wchar_t\*|系統:字串*|marshal_as|元帥.h|
|wchar_t \*|系統:字串*|marshal_as|元帥.h|
|系統::IntPtr|HANDLE|marshal_as|marshal_windows.h|
|HANDLE|系統::IntPtr|marshal_as|marshal_windows.h|
|系統:字串*|BSTR|marshal_context|marshal_windows.h|
|BSTR|系統:字串*|marshal_as|元帥.h|
|系統:字串*|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|系統:字串*|marshal_as|marshal_windows.h|
|系統:字串*|std::字串|marshal_as|marshal_cppstd.h|
|std::字串|系統:字串*|marshal_as|marshal_cppstd.h|
|系統:字串*|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|系統:字串*|marshal_as|marshal_cppstd.h|
|系統:字串*|CStringT\<字元>|marshal_as|marshal_atl.h|
|CStringT\<字元>|系統:字串*|marshal_as|marshal_atl.h|
|系統:字串*|CStringt<wchar_t>|marshal_as|marshal_atl.h|
|CStringt<wchar_t>|系統:字串*|marshal_as|marshal_atl.h|
|系統:字串*|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|系統:字串*|marshal_as|marshal_atl.h|

封送僅在從託管數據類型封送到本機數據類型且要轉換為的本機類型沒有用於自動清理的析構函數時,才需要上下文。 封送上下文銷毀其析構函數中分配的本機數據類型。 因此,需要上下文的轉換僅在刪除上下文之前才有效。 要保存任何封送值,必須將值複製到自己的變數。

> [!NOTE]
> 如果字串中嵌入`NULL`了 s,則不能保證對字串進行封送的結果。 嵌入`NULL`的 s 可能導致字串被截斷,或者可能保留它們。

此範例展示如何在包含標頭宣告中包括 msclr 目錄:

`#include "msclr\marshal_cppstd.h"`

封送庫是可擴展的,因此您可以添加自己的封送類型。 有關擴展封送庫的詳細資訊,請參閱[如何:擴展封送庫](../dotnet/how-to-extend-the-marshaling-library.md)。

## <a name="see-also"></a>另請參閱

[C++ 支援程式庫](../dotnet/cpp-support-library.md)<br/>
[如何：擴充封送處理程式庫](../dotnet/how-to-extend-the-marshaling-library.md)
