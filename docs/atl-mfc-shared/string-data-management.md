---
title: 字串資料管理
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 7f92b38ac659faef2dd9319b2f204ba837f0d473
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317456"
---
# <a name="string-data-management"></a>字串資料管理

視覺化C++提供了幾種管理字串資料的方法:

- 使用 C 樣式空終止字串的[字串](../c-runtime-library/string-manipulation-crt.md)

- 管理字串的 Win32 API 函數

- MFC 的類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md), 提供靈活、可調整大小的字串物件

- 類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md), 它提供與 MFC 無關的字串物件,其功能與`CString`

幾乎所有程式都使用字串數據。 MFC`CString`的 類通常是靈活字串處理的最佳解決方案。 從版本 7.0`CString`開始,可用於 MFC 或與 MFC 無關的程式。 運行時庫和支援`CString`字串都包含多位元組(寬)字元,如 Unicode 或 MBCS 程式設計中。

本文介紹了類庫提供的與字串操作相關的通用服務。 本文涵蓋的主題包括:

- [Unicode 和 MBCS 提供可移植性](#_core_unicode_and_mbcs_provide_portability)

- [CStrings 與 const 字元指標](#_core_cstrings_and_const_char_pointers)

- [CString 引用計數](#_core_cstring_reference_counting)

[CStringT 類](../atl-mfc-shared/reference/cstringt-class.md)支援操作字串。 它旨在替換和擴展 C 執行時庫字串包通常提供的功能。 類`CString`提供成員函數和運算符,以便簡化字串處理,類似於 Basic 中的函數和運算元。 該類還提供構造函數和運算符,用於構造、分配和比較`CString`和標準C++字串數據類型。 因為`CString`不是派生`CObject`自 ,因此可以使用`CString`獨立於大多數 Microsoft 基礎類庫 (MFC) 的物件。

`CString`物件遵循"值語義"。 物件`CString`表示唯一值。 將一`CString`個視為實際字串,而不是指向字串的指標。

物件`CString`表示可變字元數的序列。 `CString`對象可以被視為字元陣列。

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode 和 MBCS 提供可移植性

使用 MFC 版本 3.0`CString`及更高版本 時,MFC(包括 )同時為 Unicode 和多位元組字元集 (MBCS) 啟用。 通過這種支援,您可以更輕鬆地編寫可為 Unicode 或 ANSI 字元建構的可移植應用程式。 要啟用此可移植性,`CString`物件中的每個字元都為 TCHAR 類型,該字`wchar_t`元的定義 是,在生成應用程式時定義符號`char`_UNICODE,或者定義 符號。" 字元`wchar_t`寬 16 位元。 如果使用定義的符號_MBCS生成,則啟用 MBCS。 MFC 本身使用定義的_MBCS符號(用於 NAFX 庫)或_UNICODE符號(對於 UAFX 庫)構建。

> [!NOTE]
> 這個`CString`範例與字串上附帶的文章顯示了為 Unicode 可移植性正確格式化的文字字串,使用_T宏,該巨集將文字字串轉換為窗型:

`L"literal string"`

> [!NOTE]
> 編譯器將其視為 Unicode 字串。 例如，下列程式碼：

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> 如果定義_UNICODE或 ANSI 字串(如果不是)則轉換為 Unicode 字串。 有關詳細資訊,請參閱文章[Unicode 和多位元組位元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

物件`CString`最多可以存儲INT_MAX (2,147,483,647) 個字元。 TCHAR 資料類型用於獲取或`CString`設置 物件內的單個字元。 與字元陣列不同,`CString`類具有內建記憶體分配功能。 這允許`CString`物件根據需要自動增長(也就是說,您不必擔心`CString`將 物件增長到適合較長的字串)。

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings 與 const 字元指標

物件`CString`也可以像文本 C 樣式字串`PCXSTR`(如果 不在 Unicode 下,它與**const char**<strong>\*</strong>相同)。 [CSimpleStringT::運算元 PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)轉換運算元`CString`允許物件在函數調用中自由替換字元指標。 **CString( LPCWSTR** `pszSrc` **)** 建構函數允許用字元`CString`指標替換 物件。

未嘗試摺疊`CString`物件。 如果使兩`CString`個物件包含`Chicago`,例如,`Chicago`中的字元儲存在兩個位置。 (MFC 的未來版本可能並非如此,因此不應依賴它。

> [!NOTE]
> 當您需要直接存取`CString`作為指向字元的非常量指標時,請使用[CSimpleStringT:getBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT::釋放緩衝區](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成員函數。

> [!NOTE]
> 使用[CStringT:AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)和[CStringT:SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成員函數來分配和設置自動化中使用的 BSTR 物件(以前稱為 OLE 自動化)。

> [!NOTE]
> 在可能的情況下,在幀`CString`上而不是在堆上分配物件。 這樣可以節省記憶體並簡化參數傳遞。

類`CString`不作為 Microsoft 基礎類庫集合類`CString`實現,但 物件當然可以作為集合中的元素存儲。

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString 引用計數

從 MFC 版本 4.0 開始,複製[CStringT 類](../atl-mfc-shared/reference/cstringt-class.md)物件時,MFC 將遞增引用計數,而不是複製數據。 這使得按值傳遞參數和按值返回`CString`物件的效率更高。 這些操作會導致調用複製構造函數,有時不止一次調用。 增加引用計數可減少這些常見操作的開銷,並使使用`CString`選項更具吸引力。

銷毀每個副本時,原始物件的引用計數將遞減。 原始`CString`物件不會銷毀,直到其引用計數減少到零。

您可以使用`CString`成員函數[CSimpleStringT::鎖定緩衝區](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[CSimpleStringT:解鎖緩衝區](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)來禁用或啟用引用計數。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
