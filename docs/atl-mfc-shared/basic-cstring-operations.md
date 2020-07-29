---
title: 基本 CString 運算
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: fa46e82f19d87c49f652779d0e86e78549935965
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220895"
---
# <a name="basic-cstring-operations"></a>基本 CString 運算

本主題說明下列基本[CString](../atl-mfc-shared/reference/cstringt-class.md)作業：

- [從標準 C 常值字串建立 CString 物件](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [存取 CString 中的個別字元](#_core_accessing_individual_characters_in_a_cstring)

- [串連兩個 CString 物件](#_core_concatenating_two_cstring_objects)

- [比較 CString 物件](#_core_comparing_cstring_objects)

- [轉換 CString 物件](#_core_converting_cstring_objects)

`Class CString`是以類別樣板[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)為基礎。 `CString`是 **`typedef`** 的 `CStringT` 。 更精確地 `CString` 說，是 **`typedef`** *明確特製化*的 `CStringT` ，這是使用類別樣板來定義類別的常見方式。 類似定義的類別為 `CStringA` 和 `CStringW` 。

`CString`、 `CStringA` 和 `CStringW` 是在和 atlstr.h 中定義。 `CStringT`定義于 cstringt 中。

`CString`、 `CStringA` 和 `CStringW` 每個都會取得一組所定義的方法和運算子， `CStringT` 以搭配其支援的字串資料使用。 有些方法會重複，而在某些情況下，會超過 C 執行時間程式庫的字串服務。

注意： `CString` 是原生類別。 針對要在 c + +/CLI managed 專案中使用的 string 類別，請使用 `System.String` 。

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>從標準 C 常值字串建立 CString 物件

您可以將 C 樣式的常值字串指派給， `CString` 就像您可以將一個 `CString` 物件指派給另一個物件一樣。

- 將 C 常值字串的值指派給 `CString` 物件。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 將一個值指派 `CString` 給另一個 `CString` 物件。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   `CString`當物件指派給另一個物件時，會複製物件的內容 `CString` 。 因此，這兩個字串不會共用組成字串之實際字元的參考。 如需如何將物件當做值使用的詳細資訊 `CString` ，請參閱[CString 語義](../atl-mfc-shared/cstring-semantics.md)。

   > [!NOTE]
   > 若要撰寫應用程式，讓它可以針對 Unicode 或 ANSI 來編譯，請使用 _T 宏來編碼文字字串。 如需詳細資訊，請參閱[Unicode 和多位元組字元集（MBCS）支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>存取 CString 中的個別字元

您可以 `CString` 使用和方法來存取物件中的個別 `GetAt` 字元 `SetAt` 。 您也可以使用陣列元素或注標、運算子（[]），而不是 `GetAt` 取得個別的字元。 （這類似于依索引存取陣列元素，如同標準 C 樣式字串）。字元的索引值 `CString` 是以零為基底。

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>串連兩個 CString 物件

若要串連兩個 `CString` 物件，請使用串連運算子（+ 或 + =），如下所示。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

串連運算子（+ 或 + =）的至少一個引數必須是 `CString` 物件，但您可以針對其他引數使用常數位符字串（例如， `"big"` ）或 **`char`** （例如 ' x '）。

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>比較 CString 物件

的 `Compare` 方法和 = = 運算子相等 `CString` 。 `Compare`、 **operator = =**、和 `CompareNoCase` 都是 MBCS 和 Unicode 感知; `CompareNoCase` 也不區分大小寫。 的 `Collate` 方法 `CString` 區分地區設定，而且通常比更慢 `Compare` 。 `Collate`僅使用您必須遵守目前地區設定所指定之排序規則的位置。

下表顯示可用的[CString](../atl-mfc-shared/reference/cstringt-class.md)比較函式，以及它們在 C 執行時間程式庫中的對等 UNICODE/MBCS 可移植函數。

|CString 函式|MBCS 函式|Unicode 函式|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`類別樣板會定義可供使用的關聯式運算子（<、 \<=, > =、>、= = 和！ =） `CString` 。 您可以使用這些運算子來比較兩個 `CStrings` ，如下列範例所示。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>轉換 CString 物件

如需將 CString 物件轉換成其他字串類型的詳細資訊，請參閱[如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)。

## <a name="using-cstring-with-wcout"></a>搭配使用 CString 與 wcout

若要搭配使用 CString 與 `wcout` ，您必須明確地將物件轉換為， `const wchar_t*` 如下列範例所示：

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

如果沒有轉換， `cs` 會被視為 **`void*`** ，並 `wcout` 列印物件的位址。 這種行為是由樣板引數推算和多載解析之間的細微互動所造成，這些都是正確且符合 c + + 標準的。

## <a name="see-also"></a>另請參閱

[字串（ATL/MFC）](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[範本特製化](../cpp/template-specialization-cpp.md)<br/>
[如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)
