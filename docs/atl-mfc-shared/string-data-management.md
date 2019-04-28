---
title: 字串資料管理
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: b247e97f5aa6b5e85a6a6b6f57a64224a9e0f435
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252658"
---
# <a name="string-data-management"></a>字串資料管理

視覺化C++提供數種方式來管理字串資料：

- [字串操作](../c-runtime-library/string-manipulation-crt.md)處理 C 樣式 null 終止字串

- 管理字串的 Win32 API 函式

- MFC 類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)，以提供彈性、 可調整大小的字串物件

- 類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)，可獨立於 MFC 的字串物件與相同的功能 `CString`

幾乎所有的程式會使用字串資料。 MFC 的`CString`類別通常是有彈性的字串處理的最佳解決方案。 7.0 版中，為起`CString`可以用於 MFC 或 MFC 無關的程式。 這兩個執行階段程式庫和`CString`支援包含多位元組 （寬） 字元的詳細資訊，如同 Unicode 或 MBCS 程式設計的字串。

本文說明類別庫會提供字串操作相關的通用服務。 本文章涵蓋的主題包括：

- [Unicode 和 MBCS 提供可攜性](#_core_unicode_and_mbcs_provide_portability)

- [CStrings 和 const char 指標](#_core_cstrings_and_const_char_pointers)

- [CString 參考計數](#_core_cstring_reference_counting)

[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)類別支援操作字串。 它被要取代和擴充通常由 C 執行階段程式庫字串封裝所提供的功能。 `CString`類別提供成員函式和運算子來簡化的字串處理，類似於 Basic 中找到。 類別也會提供建構函式和運算子建構、 指派和比較`CString`s 和標準C++字串資料類型。 因為`CString`不衍生自`CObject`，您可以使用`CString`獨立大部分 Microsoft Foundation Class 程式庫 (MFC) 的物件。

`CString` 物件可讓您遵循"的值語意。" A`CString`物件都代表唯一的值。 把`CString`做為實際的字串，而非字串的指標。

A`CString`物件所表示的變動數目的字元序列。 `CString` 物件可以視為字元的陣列。

##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode 和 MBCS 提供可攜性

MFC 3.0 版和更新版本，MFC，包括`CString`，啟用對 Unicode 和多位元組字元集 (MBCS)。 這項支援可讓您更輕鬆地撰寫可攜式應用程式，您可以建置 Unicode 或 ANSI 字元。 若要啟用這種方便性，每個字元`CString`物件屬於下列類型 TCHAR，其定義如下`wchar_t`如果您定義符號 _UNICODE，當您建置您的應用程式，或為`char`如果不是。 A`wchar_t`字元是 16 位元寬。 如果您使用定義 _MBCS 建置，則會啟用 MBCS。 MFC 本身內建有任一個的 _MBCS 符號 （NAFX 文件庫中），或定義 _UNICODE 符號 （適用於 UAFX 文件庫中）。

> [!NOTE]
>  `CString`本篇和隨附的發行項的字串中的範例顯示 Unicode 可攜性，使用 _T 巨集，這會轉譯格式的常值字串的格式正確的常值字串：

`L"literal string"`

> [!NOTE]
>  其中，編譯器會視為 Unicode 字串。 例如，下列程式碼：

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
>  會轉譯為 Unicode 字串，如果已定義 _UNICODE 或如果沒有為 ANSI 字串。 如需詳細資訊，請參閱文章[Unicode 和多位元組字元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

A`CString`物件可以會儲存為 INT_MAX (2,147,483,647) 個字元。 TCHAR 資料類型用來取得或設定內的個別字元`CString`物件。 與不同的字元陣列，是`CString`類別具有內建的記憶體配置功能。 這可讓`CString`視需要自動成長的物件 (也就是您不必擔心成長`CString`物件大小以容納較長的字串)。

##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings 和 const char 指標

A`CString`物件也可以做為常值的 C 樣式字串 ( `PCXSTR`，這是與相同**const char** <strong>\*</strong>如果不在 Unicode 下的)。 [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)轉換運算子可讓`CString`來自由取代函式呼叫中的字元指標的物件。 **CString (LPCWSTR** `pszSrc` **)** 建構函式可讓用來取代的字元指標`CString`物件。

不會嘗試以摺疊`CString`物件。 如果您讓這兩個`CString`物件包含`Chicago`，例如，在字元`Chicago`會儲存在兩個地方。 （這可能不是真正的未來版本的 MFC，因此您不應該相依於它。）

> [!NOTE]
>  使用[CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)並[CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成員函式，當您需要直接存取`CString`為非常數的字元指標。

> [!NOTE]
>  使用[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)並[CStringT::SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)來配置及設定 BSTR 物件用於 Automation （先前稱為 OLE Automation） 的成員函式。

> [!NOTE]
>  可能的話，配置`CString`框架上，而不是在堆積上的物件。 這會節省記憶體，並簡化傳遞的參數。

`CString`未實作類別作為 Microsoft Foundation 類別程式庫集合類別，不過`CString`物件的確可以儲存為集合中的項目。

##  <a name="_core_cstring_reference_counting"></a> CString 參考計數

根據 MFC 4.0 版，當[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)複製物件，MFC 會遞增參考計數，而不是將資料複製。 這可讓傳遞參數值，並傳回`CString`值更有效率的物件。 這些作業會導致複製建構函式呼叫，有時超過一次。 遞增參考計數減少這些常見作業的負擔，並使用 「 建立`CString`更吸引人的選項。

因為每個複本被終結時，原始物件的參考計數會遞減。 原始`CString`物件並不會終結之前參考計數會減少為零。

您可以使用`CString`成員函式[CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)並[CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)停用或啟用參考計數。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
