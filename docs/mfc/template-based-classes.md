---
title: 樣板架構類別
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 29f5f815b62835aedbca1f79b797f826ea53d83b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370461"
---
# <a name="template-based-classes"></a>樣板架構類別

本文在 MFC 版本 3.0 及更高版本中介紹了基於類型安全範本的集合類。 使用這些範本創建類型安全集合比使用不基於範本的集合類更方便,並有助於更有效地提供類型安全性。

MFC 預先定義了兩類基於樣本的集合:

- [簡單的陣列、清單和地圖類別](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [類型指標的陣列、清單和映射](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

簡單集合類都派生自類`CObject`,因此它們繼承了`CObject`的 序列化、動態創建和其他屬性。 型態的指標集合類要求您指定派生自的類— 它必須是 MFC 預先定義的非樣本指標集合之一`CPtrList`,`CPtrArray`例如或 。 新的集合類從指定的基類繼承,而新類的成員函數使用對基類成員的封裝調用來強制實施類型安全。

有關C++範本的詳細資訊,請參閱*C++語言參考*中的[範本](../cpp/templates-cpp.md)。

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>使用簡單陣列、清單和地圖樣本

要使用簡單的收集範本,您需要瞭解可以在這些集合中存儲哪些類型的數據,以及集合聲明中要使用的參數。

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>簡單的陣列和清單用法

簡單的數位與清單類別[CArray](../mfc/reference/carray-class.md)與[CList](../mfc/reference/clist-class.md)採用兩個參數`ARG_TYPE`*:TYPE*與 。 這些類別可以儲存您在*TYPE*參數中指定的任何資料類型:

- 基本C++資料類型,如**int**、**字元**與**浮點**

- C++結構和類

- 您定義的其他類型

為方便和效率,可以使用*ARG_TYPE*參數指定函數參數的類型。 通常,ARG_TYPE指定*為*對*TYPE*參數中命名類型的引用。 例如：

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

第一個範例的宣告`myArray`包含**int**s 的陣列集合 。 第二個範例`myList``CPerson`的清單集合 。 集合類的某些成員函數採用其類型由*ARG_TYPE*範本參數指定的參數。 例如,`Add``CArray`類別的成員函數以*ARG_TYPE*參數:

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>簡易地圖使用

簡單的地圖類別[CMap](../mfc/reference/cmap-class.md)採用四個參數:*鍵**、ARG_KEY、VALUE*和*ARG_VALUE*。 *VALUE* 與陣列和清單類一樣,地圖類可以存儲任何數據類型。 與陣列和清單(哪個陣列和清單)(它們儲存的數據編製索引和排序)不同,映射關聯鍵和值:通過指定值的關聯鍵來存取存儲在地圖中的值。 *KEY*參數指定用於存取儲存在地圖中的數據的鍵的資料類型。 如果*KEY*的類型是結構或類別,*則ARG_KEY*參數通常是對*KEY*中指定的類型的引用。 *VALUE*參數指定存儲在地圖中的項的類型。 如果*ARG_VALUE*的類型是結構或類,*則ARG_VALUE*參數通常是對*VALUE*中指定的類型的引用。 例如：

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

第一個示例`MY_STRUCT`存儲值,通過**int**鍵訪問值,`MY_STRUCT`並通過引用 返回訪問的專案。 第二個範例`CPerson`儲存值,`CString`按鍵訪問值,並返回對已訪問項的引用。 此示例可能表示一個簡單的通訊錄,您可以在其中按姓氏查找人員。

由於*KEY*KEY`CString`參數的類型和*KEY_TYPE*`LPCSTR`參數的類型,因此`CString`鍵作為類型的項存儲在地圖中,但在函數`SetAt`中引用,`LPCSTR`例如 通過類型的指標。 例如：

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>使用鍵入指標收集樣本

要使用類型化指標集合樣本,您需要瞭解可以在這些集合中存儲哪些類型的數據,以及集合聲明中要使用的參數。

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>鍵入指標的陣列與清單使用方式

類型指標數組與清單類別[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)與[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)採用兩個參數 *:BASE_CLASS*和*TYPE*。 這些類可以儲存您在*TYPE*參數中指定的任何數據類型。 它們派生自存儲指標的非範本集合類之一;在*BASE_CLASS*中指定此基類。 對陣列,請使用或`CObArray``CPtrArray`。 對清單,請使用`CObList`或`CPtrList`。

實際上,當您基於,例如`CObList`,宣佈集合時,新類不僅繼承其基類的成員,而且還聲明許多額外的類型安全成員函數和運算符,這些函數和運算符通過封裝對基類成員的調用來説明提供類型安全性。 這些封裝管理所有必要的類型轉換。 例如：

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

第一個範例指針陣列集`myArray`自`CObArray`。 數位儲存並返回指向`CPerson`物件的指標(其中`CPerson`是從派生的`CObject`類)。 您可以`CObArray`呼叫任何成員函數,也可以呼叫新的`GetAt`型態`ElementAt`安全函數 或使用型態安全 ***運算子**。

第二個示例聲明從`myList``CPtrList`派生的鍵入的指標清單。 該清單存儲並返回指向`MY_STRUCT`物件的指標。 基於的`CPtrList`類用於存儲指向未派生自`CObject`的物件的指標。 `CTypedPtrList`具有許多類型`GetHead`安全成員函數: `GetTail` `RemoveHead`、 `RemoveTail` `GetNext` `GetPrev`、`GetAt`、 、 、 和 。

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>鍵入指標對應使用方式

類型指標對應類別[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)的參數 *:BASE_CLASS、**鍵*與*VALUE*。 *BASE_CLASS*參數指定從中派生新`CMapPtrToWord`類 的類`CMapPtrToPtr`: `CMapStringToPtr` `CMapWordToPtr` `CMapStringToOb`、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 、 *KEY*與*KEY*`CMap`中的 KEY 類似:它指定用於搜尋的金鑰的類型。 *VALUE*類似於`CMap`中的*VALUE,* 它指定儲存在地圖中的物件類型。 例如：

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

第一個範例是基於`CMapPtrToPtr`的映射,`CString`它使用對應到指向`MY_STRUCT`的指標的鍵。 您可以通過調用類型`Lookup`安全 成員函數來查找存儲的指標。 您可以使用 ***運算子**尋找儲存的指標,如果找不到,則添加它。 您可以使用類型安全`GetNextAssoc`函數反覆運算地圖。 您還可以調用類`CMapPtrToPtr`的其他成員函數。

第二個範例是基於`CMapStringToOb`的映射, 它使用對應到儲存到`CMyObject`物件的指標的字串鍵。 您可以使用上一段中描述的相同類型安全成員,也可以調用類`CMapStringToOb`的成員 。

> [!NOTE]
> 如果為*VALUE*參數指定**類**或**結構**類型,而不是指向該類型的指標或引用,則類或結構必須具有複製構造函數。

有關詳細資訊,請參閱[如何建立類型安全集合](../mfc/how-to-make-a-type-safe-collection.md)。

## <a name="see-also"></a>另請參閱

[集合](../mfc/collections.md)
