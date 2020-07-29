---
title: 字串資料管理
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: 2da8967effeb6ff439cf5b3cece31f63ee77a761
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219036"
---
# <a name="string-data-management"></a>字串資料管理

Visual C++ 提供數種方式來管理字串資料：

- 使用 C 樣式 null 終止字串的[字串操作](../c-runtime-library/string-manipulation-crt.md)

- 用於管理字串的 WIN32 API 函式

- MFC 的類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)，提供彈性且可調整大小的字串物件

- 類別[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)，它會提供與相同功能的 MFC 獨立字串物件`CString`

幾乎所有程式都會使用字串資料。 MFC 的 `CString` 類別通常是彈性字串處理的最佳解決方案。 從7.0 版開始， `CString` 可以在 mfc 或 mfc 獨立的程式中使用。 執行時間程式庫和 `CString` 支援包含多位元組（寬）字元的字串，如 Unicode 或 MBCS 程式設計中所示。

本文說明類別庫提供與字串操作相關的一般用途服務。 本文涵蓋的主題包括：

- [Unicode 和 MBCS 提供可攜性](#_core_unicode_and_mbcs_provide_portability)

- [CStrings 和 const char 指標](#_core_cstrings_and_const_char_pointers)

- [CString 參考計數](#_core_cstring_reference_counting)

[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)會提供操作字串的支援。 其目的是要取代並擴充 C 執行時間程式庫字串封裝一般提供的功能。 `CString`類別會提供成員函式和運算子，以進行簡化的字串處理，類似于在 Basic 中找到的函數。 類別也會提供用來建立 `CString` 和比較和標準 c + + 字串資料類型的函數和運算子。 因為 `CString` 並非衍生自 `CObject` ，所以您可以使用 `CString` 與大部分 MFC 程式庫（MFC）無關的物件。

`CString`物件會遵循「值的語義」。 `CString`物件代表唯一的值。 將 `CString` 視為實際的字串，而不是字串的指標。

`CString`物件代表可變字元數的序列。 `CString`可以將物件視為字元陣列。

## <a name="unicode-and-mbcs-provide-portability"></a><a name="_core_unicode_and_mbcs_provide_portability"></a>Unicode 和 MBCS 提供可攜性

使用 MFC 版本3.0 和更新版本 `CString` 時，會同時啟用 Unicode 和多位元組字元集（MBCS）的 mfc （包括）。 這項支援可讓您更輕鬆地撰寫可針對 Unicode 或 ANSI 字元建立的可移植應用程式。 若要啟用這種可攜性，物件中的每個字元 `CString` 都屬於 TCHAR 類型，定義為 **`wchar_t`** 您在建立應用程式時定義符號 _UNICODE，否則為 **`char`** 。 **`wchar_t`** 字元是16位寬。 如果您使用 _MBCS 定義的符號建立，則會啟用 MBCS。 MFC 本身是以 _MBCS 符號（適用于 NAFX 程式庫）或定義的 _UNICODE 符號（適用于 UAFX 程式庫）所建立。

> [!NOTE]
> `CString`這篇文章中的範例以及有關字串的隨附發行項，會使用 _T 宏（會將常值字串轉譯成格式），來顯示正確格式化 Unicode 可攜性的常值字串：

`L"literal string"`

> [!NOTE]
> 編譯器會將其視為 Unicode 字串。 例如，下列程式碼：

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
> 如果已定義 _UNICODE，則會轉譯為 Unicode 字串，如果不是則為 ANSI 字串。 如需詳細資訊，請參閱[Unicode 和多位元組字元集（MBCS）支援一](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)文。

`CString`物件最多可以儲存 INT_MAX （2147483647）個字元。 TCHAR 資料類型是用來取得或設定物件內的個別字元 `CString` 。 與字元陣列不同的是， `CString` 類別具有內建的記憶體配置功能。 這可讓 `CString` 物件視需要自動成長（也就是您不需要擔心增加 `CString` 物件以容納較長的字串）。

## <a name="cstrings-and-const-char-pointers"></a><a name="_core_cstrings_and_const_char_pointers"></a>CStrings 和 const char 指標

`CString`物件也可以像常值 C 樣式字串（a `PCXSTR` ，這與**const char** （ <strong>\*</strong> 如果不在 Unicode 底下）相同）。 [CSimpleStringT：： OPERATOR PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)轉換運算子允許 `CString` 在函式呼叫中自由取代字元指標的物件。 **CString （LPCWSTR** `pszSrc` **）** 函數可讓字元指標取代 `CString` 物件。

不會嘗試折迭 `CString` 物件。 例如，如果您建立兩個 `CString` 包含的物件 `Chicago` ，則中的字元 `Chicago` 會儲存在兩個位置。 （這在 MFC 的未來版本中可能不適用，因此您不應該依賴它）。

> [!NOTE]
> 當您需要直接存取做為字元的非常數指標時，請使用[CSimpleStringT：： GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)和[CSimpleStringT：： ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)成員函式 `CString` 。

> [!NOTE]
> 使用[CStringT：： AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)和[CStringT：： SetSysString](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)成員函式來配置及設定自動化中使用的 BSTR 物件（先前稱為 OLE Automation）。

> [!NOTE]
> 可能的話，請在 `CString` 框架上設定物件，而不是在堆積上。 這可節省記憶體並簡化參數傳遞。

`CString`類別不會實作為 MFC 程式庫集合類別，不過 `CString` 物件當然可以儲存為集合中的元素。

## <a name="cstring-reference-counting"></a><a name="_core_cstring_reference_counting"></a>CString 參考計數

從 MFC 版本4.0，複製[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)物件時，MFC 會遞增參考計數，而不會複製資料。 這會以傳值方式傳遞參數，並 `CString` 以更有效率的值傳回物件。 這些作業會導致呼叫複製的構造函式，有時會多次。 遞增參考計數可減少這些常見作業的額外負荷，並使用 `CString` 更具吸引力的選項。

當每個複本損毀時，原始物件中的參考計數就會遞減。 原始 `CString` 物件在其參考計數縮減為零之前，不會終結。

您可以使用 `CString` 成員函式[CSimpleStringT：： LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[CSimpleStringT：： UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)來停用或啟用參考計數。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
