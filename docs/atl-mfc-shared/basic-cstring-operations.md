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
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317953"
---
# <a name="basic-cstring-operations"></a>基本 CString 運算

本主題介紹以下基本[CString](../atl-mfc-shared/reference/cstringt-class.md)操作:

- [從標準 C 文字字串建立 CString 物件](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [存取 CString 的單個字元](#_core_accessing_individual_characters_in_a_cstring)

- [串聯兩個 CString 物件](#_core_concatenating_two_cstring_objects)

- [比較 CString 物件](#_core_comparing_cstring_objects)

- [轉換 CString 物件](#_core_converting_cstring_objects)

`Class CString`基於類別樣本[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)。 `CString``CStringT`**是的型態定義**。 更確切地說`CString`,`CStringT`是 的*顯式專門化*的類型**定義**,這是使用類範本定義類的常用方法。 同樣定義的類別是`CStringA``CStringW`與 。

`CString``CStringA`,並在`CStringW`atlstr.h 中定義。 `CStringT`在 cstringt.h 中定義。

`CString`,`CStringA``CStringW`每個 獲取一`CStringT`組定義 的方法和運算符,以便與它們支援的字串數據一起使用。 有些方法重複,在某些情況下,超過了 C 運行時庫的字串服務。

注意:`CString`是本機類。 對 G+/CLI 託管專案中的字串類別,請使用`System.String`。

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>從標準 C 文字字串建立 CString 物件

您可以將 C 樣式文字字串分配給`CString`a, 就像您可以將`CString`一個物件 分配給另一個物件一樣。

- 將 C 文字字串的值分配`CString`給 物件。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 將一個`CString`物件的值分配給`CString`另 一個物件。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   當一個物件`CString`分配給另一`CString`個 物件時,將複製物件的內容。 因此,這兩個字串不共用對構成字串的實際字元的引用。 有關如何將物件用作`CString`值的詳細資訊,請參閱[CString 語義](../atl-mfc-shared/cstring-semantics.md)。

   > [!NOTE]
   > 編寫應用程式以便可以編譯為 Unicode 或 ANSI,請使用_T巨集編寫文字字串。 有關詳細資訊,請參閱[Unicode 和多位元組位元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>存取 CString 的單個字元

可以使用和方法訪問物件`CString``GetAt``SetAt`中的單個字元。 您還可以使用陣列元素或下標運算符 ( *`GetAt`) 而不是 獲取單個字元。 (這類似於按索引訪問陣列元素,如標準 C 樣式字串中。字元的`CString`索引值是零基的。

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>串聯兩個 CString 物件

要串聯兩`CString`個物件,請使用串聯運算符 (* 或 *),如下所示。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

對串聯運算符(* 或 +)的至少一`CString`個 參數必須是物件,但可以使用常量字串(`"big"`例如 )或**字元**(例如,"x")作為另一個參數。

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>比較 CString 物件

方法和`Compare`* 運算`CString`子 等效。 `Compare`,**運算符**=`CompareNoCase`, 並且是 MBCS 和 Unicode 感知;`CompareNoCase`也區分大小寫。 的方法`Collate``CString`對區域設定敏感,通常比`Compare`慢 。 僅在`Collate`必須遵守當前區域設置指定的排序規則的情況下使用。

下表顯示了 C 執行時庫中可用的[CString](../atl-mfc-shared/reference/cstringt-class.md)比較函數及其等效的 Unicode/MBCS 可移植函數。

|CString 函數|MBCS 功能|Unicode 函數|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

類`CStringT`模板定義關係運算符(<、*、>\<*、>、*和 !"),這些運算符可`CString`供 使用。 您可以使用這些運算元比較`CStrings`兩個,如以下範例所示。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>轉換 CString 物件

有關將 CString 物件轉換為其他字串型態的資訊,請參考[如何:在各種字串型態之間進行轉換](../text/how-to-convert-between-various-string-types.md)。

## <a name="using-cstring-with-wcout"></a>將 CString 與 wcout 一起使用

要將 CString`wcout`與 一起使用,必須`const wchar_t*`顯式將 物件強制轉換為 a,如以下範例所示:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

如果沒有強制轉換,`cs`將被視為`void*``wcout`並列印對象的位址。 此行為是由範本參數推導和重載解析之間的微妙交互引起的,這些交互本身是正確的,並且符合C++標準。

## <a name="see-also"></a>另請參閱

[字串(ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[範本特製化](../cpp/template-specialization-cpp.md)<br/>
[如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)
