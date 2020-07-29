---
title: 使用 CString
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: 8ebf3441c7d8856fe412e2efed4c717b01ced362
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219010"
---
# <a name="using-cstring"></a>使用 CString

本節中的主題會描述如何使用 `CString` 進行程式設計。 如需類別的參考檔 `CString` ，請參閱[CStringT](../atl-mfc-shared/reference/cstringt-class.md)的檔。

若要使用 `CString`，請包括 `atlstr.h` 標頭。

`CString`、和類別是類別樣板的特製化， `CStringA` `CStringW` 稱為[CStringT](../atl-mfc-shared/reference/cstringt-class.md) ，以其所支援的字元資料類型為基礎。

`CStringW`物件包含型別 **`wchar_t`** 並支援 Unicode 字串。 `CStringA`物件包含型別 **`char`** ，而且支援單一位元組和多位元組（MBCS）字串。 `CString`物件支援 **`char`** 型別或型別 **`wchar_t`** ，視 MBCS 符號或 UNICODE 符號是否在編譯時期定義而定。

`CString` 物件會在 `CStringData` 物件中保留字元資料。 `CString`接受以 Null 結束的 C 樣式字串。 `CString`追蹤字串長度以提高效能，但也會保留儲存字元資料中的 Null 字元，以支援轉換成 LPCWSTR。 `CString`會在匯出 C 樣式字串時包含 null 結束字元。 您可以在中的其他位置插入 Null `CString` ，但可能會產生非預期的結果。

使用下列字串類別集時，可以不連結 MFC 程式庫、及具有或不具有 CRT 支援：`CAtlString`、`CAtlStringA` 和 `CAtlStringW`。

`CString` 在原生專案中使用。 對於 Managed 程式碼 (C++/CLI) 專案，請使用 `System::String`。

若要加入比 `CString`、`CStringA` 或 `CStringW` 目前提供的更多功能，您應該建立包含其他功能的 `CStringT` 子類別。

下列程式碼會顯示如何建立 `CString`，且將其列印至標準輸出：

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>本節內容

[基本 CString 作業](../atl-mfc-shared/basic-cstring-operations.md)<br/>
描述基本 `CString` 作業，包括從 C 常值字串建立物件，存取 `CString` 中的個別字元，串連兩個物件，以及比較 `CString` 物件。

[字串資料管理](../atl-mfc-shared/string-data-management.md)<br/>
討論如何將 Unicode 及 MBCS 與 `CString` 搭配使用。

[CString 語義](../atl-mfc-shared/cstring-semantics.md)<br/>
解釋如何使用 `CString` 物件。

[與 C 樣式字串相關的 CString 作業](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
描述如何使用類似 C 樣式 null 結尾字串的方式，來操作 `CString` 物件的內容。

[配置和釋放 BSTR 的記憶體](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
討論如何針對 BSTR 和 COM 物件使用記憶體。

[CString 例外狀況清除](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
解釋 MFC 3.0 及以後版本中不再需要明確清除。

[CString 引數傳遞](../atl-mfc-shared/cstring-argument-passing.md)<br/>
解釋如何將 CString 物件傳遞至函式，以及如何從函式傳回 `CString` 物件。

[Unicode 和多位元組字元集（MBCS）支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
討論如何針對 Unicode 及 MBCS 支援啟用 MFC。

## <a name="reference"></a>參考

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
提供 `CStringT` 類別的參考資訊。

[CSimpleStringT 類別](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
提供 `CSimpleStringT` 類別的參考資訊。

## <a name="related-sections"></a>相關章節

[字串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
包含各主題的連結，描述管理字串資料的數個方法。

[字串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)
