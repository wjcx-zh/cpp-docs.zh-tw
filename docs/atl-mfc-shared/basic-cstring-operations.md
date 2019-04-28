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
ms.openlocfilehash: 08c496038efc9e24e1c1610da07b6824c3a50b64
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62216853"
---
# <a name="basic-cstring-operations"></a>基本 CString 運算

本主題說明下列基本[CString](../atl-mfc-shared/reference/cstringt-class.md)作業：

- [從標準 C 常值字串建立 CString 物件](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [存取 CString 中的個別字元](#_core_accessing_individual_characters_in_a_cstring)

- [串連兩個 CString 物件](#_core_concatenating_two_cstring_objects)

- [比較 CString 物件](#_core_comparing_cstring_objects)

- [轉換 CString 物件](#_core_converting_cstring_objects)

`Class CString` 類別範本為基礎[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)。 `CString` 已**typedef**的`CStringT`。 更精確地`CString`已**typedef**的*明確特製化*的`CStringT`，這是常見的方式來使用類別樣板定義的類別。 同樣地定義類別`CStringA`和`CStringW`。

`CString``CStringA`，和`CStringW`和中所定義。 `CStringT` 定義於 cstringt.h。

`CString``CStringA`，並`CStringW`各取得一組方法和所定義的運算子`CStringT`與它們所支援的字串資料搭配使用。 某些方法重複，在某些情況下，大於字串的服務的 C 執行階段程式庫。

注意：`CString`是原生類別。 字串類別是用於C++/CLI 受控專案中，使用`System.String`。

##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> 從標準 C 常值字串建立 CString 物件

您可以指派到 C 樣式常值字串`CString`就像您可以指派其中`CString`到另一個物件。

- C 常值字串的值指派`CString`物件。

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- 其中一個值指派`CString`到另一個`CString`物件。

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   內容`CString`時，會複製物件`CString`物件指派給另一個。 因此，兩個字串不會共用的實際字元字串所組成的參考。 如需有關如何使用`CString`物件做為值，請參閱[CString 語意](../atl-mfc-shared/cstring-semantics.md)。

   > [!NOTE]
   > 若要撰寫您的應用程式，使它可以編譯為 Unicode 或 ANSI，程式碼使用 _T 巨集的常值字串。 如需詳細資訊，請參閱 < [Unicode 和多位元組字元集 (MBCS) 支援](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)。

##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> 存取 CString 中的個別字元

您可以存取中的個別字元`CString`使用的物件`GetAt`和`SetAt`方法。 您也可以使用陣列項目或註標運算子 ([])，而不是`GetAt`取得個別字元。 （這類似於存取陣列元素的索引，如同標準的 C 樣式字串。）編製索引的值`CString`字元以零為起始。

##  <a name="_core_concatenating_two_cstring_objects"></a> 串連兩個 CString 物件

要串連兩個`CString`物件，使用串連運算子 (+ 或 + =)、，如下所示。

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

至少一個引數的串連運算子 (+ 或 + =) 必須是`CString`物件，但您可以使用常數的字元字串 (例如`"big"`) 或**char** (例如，' x') 的其他引數。

##  <a name="_core_comparing_cstring_objects"></a> 比較 CString 物件

`Compare`方法而 = = 運算子`CString`相等。 `Compare`**運算子 = =**，和`CompareNoCase`是 MBCS 和 Unicode 感知;`CompareNoCase`也是不區分大小寫。 `Collate`方法`CString`區分地區設定而通常低於`Compare`。 使用`Collate`目前的地區設定所述的步驟只有其中一些必須遵守排序規則。

下表顯示可用[CString](../atl-mfc-shared/reference/cstringt-class.md)比較函式和其對等的 Unicode/MBCS 可攜式函式，C 執行階段程式庫中。

|CString 函式|MBCS 函式|Unicode 函式|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT`類別樣板定義關係運算子 (<， \<=、 > =、 >、 = =、 和 ！ =)，這是可供使用`CString`。 您可以比較兩個`CStrings`使用這些運算子，如下列範例所示。

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

##  <a name="_core_converting_cstring_objects"></a> 轉換 CString 物件

如需將 CString 物件轉換成其他字串類型的詳細資訊，請參閱[How to:各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)。

## <a name="using-cstring-with-wcout"></a>使用 CString wcout 與

若要使用與 CString`wcout`您必須明確地將物件轉換成`const wchar_t*`如下列範例所示：

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

沒有轉型，`cs`會被視為`void*`和`wcout`列印物件的位址。 此行為起因於樣板引數推算和多載解析中正確本身與符合之間的微妙互動C++標準。

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT 類別](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[範本特製化](../cpp/template-specialization-cpp.md)<br/>
[如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)
