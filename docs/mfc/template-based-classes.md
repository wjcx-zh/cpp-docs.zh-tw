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
ms.openlocfilehash: eceee4421b43515b9b246f4af26a1a3741c6b25b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230450"
---
# <a name="template-based-classes"></a>樣板架構類別

本文說明 MFC 3.0 版和更新版本中的型別安全範本型集合類別。 使用這些範本建立型別安全集合比較方便，而且可以比使用不是以範本為基礎的集合類別更有效率地提供型別安全性。

MFC 會預先定義兩個以範本為基礎的集合類別：

- [簡單的陣列、清單和對應類別](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`, `CList`, `CMap`

- [具類型指標的陣列、清單和對應](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`

簡單的集合類別全都衍生自類別 `CObject` ，因此它們會繼承的序列化、動態建立和其他屬性 `CObject` 。 具類型的指標集合類別會要求您指定衍生自的類別，這必須是 MFC 預先定義的其中一個非範本指標集合，例如 `CPtrList` 或 `CPtrArray` 。 新的集合類別繼承自指定的基類，而新類別的成員函式會使用基類成員的封裝呼叫來強制型別安全。

如需 c + + 範本的詳細資訊，請參閱*c + + 語言參考*中的[範本](../cpp/templates-cpp.md)。

## <a name="using-simple-array-list-and-map-templates"></a><a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>使用簡單陣列、清單和對應範本

若要使用簡單的集合範本，您必須知道可以在這些集合中儲存的資料類型，以及要在集合宣告中使用的參數。

### <a name="simple-array-and-list-usage"></a><a name="_core_simple_array_and_list_usage"></a>簡單陣列和清單使用方式

簡單陣列和清單類別[CArray](../mfc/reference/carray-class.md)和[CList](../mfc/reference/clist-class.md)會接受兩個參數：*輸入*和 `ARG_TYPE` 。 這些類別可以儲存您在*型*別參數中指定的任何資料型別：

- 基本 c + + 資料類型，例如 **`int`** 、 **`char`** 和**`float`**

- C + + 結構和類別

- 您定義的其他類型

為了方便和提高效率，您可以使用*ARG_TYPE*參數來指定函數引數的類型。 一般來說，您會將*ARG_TYPE*指定為您在*型*別參數中命名之型別的參考。 例如：

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

第一個範例會宣告陣列集合， `myArray` 其中包含 **`int`** s。 第二個範例會宣告一個 `myList` 可儲存物件的清單集合 `CPerson` 。 集合類別的某些成員函式會採用其類型是由*ARG_TYPE*樣板參數所指定的引數。 例如，類別的 `Add` 成員函 `CArray` 式會採用*ARG_TYPE*引數：

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

### <a name="simple-map-usage"></a><a name="_core_simple_map_usage"></a>簡單對應使用方式

簡單的 map 類別[CMap](../mfc/reference/cmap-class.md)會採用四個參數：索引*鍵*、 *ARG_KEY*、*值*和*ARG_VALUE*。 如同陣列和清單類別，map 類別可以儲存任何資料類型。 不同于陣列和清單（索引和排序它們所儲存的資料），maps 會關聯索引鍵和值：您可以藉由指定值的關聯金鑰來存取儲存在對應中的值。 *KEY*參數會指定用來存取儲存在對應中之資料的索引鍵資料類型。 如果索引*鍵*的類型是結構或類別，則*ARG_KEY*參數通常是索引*鍵*中所指定類型的參考。 *VALUE*參數會指定儲存在對應中的專案類型。 如果*ARG_VALUE*的類型是結構或類別，則*ARG_VALUE*參數通常是 [*值*] 中指定之類型的參考。 例如：

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

第一個範例會儲存 `MY_STRUCT` 值、依索引 **`int`** 鍵存取，並以傳址方式傳回存取的 `MY_STRUCT` 專案。 第二個範例會儲存 `CPerson` 值、依索引鍵進行存取 `CString` ，以及傳回存取專案的參考。 這個範例可能代表一個簡單的通訊錄，您可以在其中依姓氏查閱人員。

因為索引*鍵*參數的類型是 `CString` ，而*KEY_TYPE*參數的類型是 `LPCSTR` ，所以索引鍵會以類型的專案形式儲存在對應中， `CString` 但會在函式中參考，例如 `SetAt` 透過類型的指標 `LPCSTR` 。 例如：

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

## <a name="using-typed-pointer-collection-templates"></a><a name="_core_using_typed.2d.pointer_collection_templates"></a>使用具類型的指標集合範本

若要使用具類型的指標集合範本，您必須知道可以在這些集合中儲存哪些類型的資料，以及要在集合宣告中使用的參數。

### <a name="typed-pointer-array-and-list-usage"></a><a name="_core_typed.2d.pointer_array_and_list_usage"></a>具類型的指標陣列和清單使用方式

具類型的指標陣列和清單類別[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)和[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)會接受兩個參數： *BASE_CLASS*和*類型*。 這些類別可以儲存您在*型*別參數中指定的任何資料型別。 它們是從儲存指標的其中一個非樣板集合類別衍生而來。您會在*BASE_CLASS*中指定這個基類。 如果是陣列，請使用 `CObArray` 或 `CPtrArray` 。 針對 [清單]，使用 `CObList` 或 `CPtrList` 。

實際上，當您根據來宣告集合時， `CObList` 新的類別不只會繼承其基類的成員，還會宣告一些額外的型別安全成員函式和運算子，藉由將呼叫封裝至基類成員，協助提供型別安全。 這些 encapsulations 會管理所有必要的類型轉換。 例如：

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

第一個範例會宣告具類型的指標陣列， `myArray` 衍生自 `CObArray` 。 陣列會儲存並傳回物件的指標 `CPerson` （其中 `CPerson` 是衍生自的類別 `CObject` ）。 您可以呼叫任何 `CObArray` 成員函式，也可以呼叫新的型別安全 `GetAt` 和 `ElementAt` 函數，或使用類型安全的 **[]** 運算子。

第二個範例會宣告具類型的指標清單， `myList` 衍生自 `CPtrList` 。 此清單會儲存並傳回 `MY_STRUCT` 物件的指標。 以為基礎的類別 `CPtrList` 是用來儲存非衍生自之物件的指標 `CObject` 。 `CTypedPtrList`具有一些型別安全成員函式： `GetHead` 、 `GetTail` 、 `RemoveHead` 、 `RemoveTail` 、 `GetNext` 、 `GetPrev` 和 `GetAt` 。

### <a name="typed-pointer-map-usage"></a><a name="_core_typed.2d.pointer_map_usage"></a>類型指標對應使用方式

具類型的指標對應類別[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)會採用三個參數： *BASE_CLASS*、索引*鍵*和*值*。 *BASE_CLASS*參數會指定要從中衍生新類別的類別： `CMapPtrToWord` 、 `CMapPtrToPtr` 、、、 `CMapStringToPtr` 等等 `CMapWordToPtr` `CMapStringToOb` 。 索引*鍵*類似于*中的索引鍵* `CMap` ：它會指定用於查閱的索引鍵類型。 *值*類似于中*VALUE*的值 `CMap` ：它會指定儲存在對應中的物件類型。 例如：

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

第一個範例是以為基礎的對應 `CMapPtrToPtr` ，它會使用 `CString` 對應至指標的索引鍵 `MY_STRUCT` 。 您可以藉由呼叫型別安全成員函式來查閱已儲存的指標 `Lookup` 。 您可以使用 **[]** 運算子查閱已儲存的指標，並在找不到時加以新增。 而且您可以使用類型安全函式來逐一查看對應 `GetNextAssoc` 。 您也可以呼叫類別的其他成員函式 `CMapPtrToPtr` 。

第二個範例是以為基礎的對應 `CMapStringToOb` ，它會使用對應至物件之儲存指標的字串索引鍵 `CMyObject` 。 您可以使用上一段所述的相同型別安全成員，也可以呼叫類別的成員 `CMapStringToOb` 。

> [!NOTE]
> 如果您 **`class`** **`struct`** 為*值*參數指定或類型，而不是對類型的指標或參考，則類別或結構必須有複製的「建立程式」。

如需詳細資訊，請參閱[如何建立型別安全集合](../mfc/how-to-make-a-type-safe-collection.md)。

## <a name="see-also"></a>另請參閱

[集合](../mfc/collections.md)
