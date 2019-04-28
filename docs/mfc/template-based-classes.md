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
ms.openlocfilehash: 40633c8b2b09d27e97443364ed3ce711ee217e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306374"
---
# <a name="template-based-classes"></a>樣板架構類別

這篇文章說明 MFC 3.0 版和更新版本中的型別安全範本型集合類別。 使用這些範本來建立類型安全集合更方便且有助於比使用非根據樣板的集合類別更有效率地提供型別安全。

MFC 預先定義範本為基礎的集合的兩個的類別：

- [簡單陣列、 清單和對應類別](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`、`CList`、`CMap`

- [陣列、 清單和對應的具類型的指標](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`、`CTypedPtrList`、`CTypedPtrMap`

簡單集合類別衍生自類別`CObject`，因此它們在繼承序列化、 動態建立，以及其他屬性的`CObject`。 具類型的指標集合類別會要求您指定衍生自的類別，它必須是其中一個預先定義的 mfc，例如非範本指標集合`CPtrList`或`CPtrArray`。 新的集合類別繼承自指定的基底類別，以及新的類別成員函式會使用基底類別成員的封裝的呼叫來強制執行型別安全。

如需詳細資訊C++範本，請參閱[範本](../cpp/templates-cpp.md)中*C++語言參考*。

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 使用簡單的陣列、 清單和對應範本

若要使用的簡單集合範本，您需要知道這些集合中可以儲存的資料類型，以及在您的集合宣告中使用哪些參數。

###  <a name="_core_simple_array_and_list_usage"></a> 簡單陣列和清單的使用方式

簡單陣列和清單類別[CArray](../mfc/reference/carray-class.md)並[CList](../mfc/reference/clist-class.md)，採用兩個參數：*型別*和`ARG_TYPE`。 這些類別可以儲存任何資料類型，您在中指定*型別*參數：

- 基本C++資料類型，例如**int**， **char**，和**浮點數**

- C++結構和類別

- 您所定義的其他型別

為了方便和效率，您可以使用*arg_type 這個*參數來指定函式引數的型別。 一般而言，您指定*arg_type 這個*做為參考您在名為的型別*型別*參數。 例如：

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

第一個範例會宣告陣列集合， `myArray`，其中包含**int**s。 第二個範例會宣告清單集合`myList`，儲存`CPerson`物件。 集合類別的特定成員函式不接受引數所指定型別*arg_type 這個*樣板參數。 例如，`Add`類別成員函式`CArray`採用*arg_type 這個*引數：

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> 簡單對應使用方式

簡單的對應類別[CMap](../mfc/reference/cmap-class.md)，接受四個參數：*索引鍵*， *ARG_KEY*，*值*，和*ARG_VALUE*。 Array 和 list 類別一樣，對應的類別可以儲存任何資料類型。 不同於陣列和清單會編製索引，並排序它們所儲存的資料，maps 將相關聯索引鍵和值：您存取儲存在 map 中所指定的值相關聯的索引鍵的值。 *金鑰*參數會指定用來存取資料儲存在 map 中索引鍵的資料類型。 如果的型別*金鑰*結構或類別*ARG_KEY*參數通常是在指定的型別參考*金鑰*。 *值*參數會指定儲存在 map 中的項目類型。 如果類型*ARG_VALUE*結構或類別*ARG_VALUE*參數通常是在指定的型別參考*值*。 例如: 

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

第一個範例存放區`MY_STRUCT`值，存取它們所**int**金鑰和存取傳回`MY_STRUCT`所參考的項目。 第二個範例存放區`CPerson`值，這兩者存取`CString`鍵，並傳回存取項目的參考。 此範例中，可能代表簡單的通訊錄，在其中您查閱的人員姓氏。

因為*金鑰*參數的類型是`CString`並*KEY_TYPE*參數的類型是`LPCSTR`，金鑰時，會儲存在對應上，為類型的項目`CString`但卻會參考這類函式`SetAt`類型的指標透過`LPCSTR`。 例如: 

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> 使用型別指標集合範本

若要使用的型別指標集合範本，您需要知道您可以儲存這些集合中的哪些類型的資料，以及在您的集合宣告中使用哪些參數。

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> 型別指標陣列和清單的使用方式

型別指標陣列和清單類別[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)並[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)，採用兩個參數：*BASE_CLASS*並*型別*。 這些類別可以儲存任何資料類型，您在中指定*型別*參數。 它們被衍生自其中一個會將指標; 儲存的非樣板集合類別指定在此基底類別*BASE_CLASS*。 陣列，請使用任何一種`CObArray`或`CPtrArray`。 如需清單，請使用任何一種`CObList`或`CPtrList`。

實際上，當您宣告為基礎的集合，說出`CObList`，新的類別不只會繼承其基底類別成員，但它也會宣告一些其他的型別安全成員函式和運算子，幫助提供類型安全，藉由將封裝呼叫基底類別成員。 這些封裝會管理所有所需的型別轉換。 例如：

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

第一個範例會宣告一個型別指標的陣列，`myArray`衍生自`CObArray`。 儲存陣列，並傳回指標`CPerson`物件 (其中`CPerson`類別衍生自`CObject`)。 您可以呼叫任何`CObArray`成員函式，或者您可以呼叫新的型別安全`GetAt`並`ElementAt`函式，或使用型別安全 **[]** 運算子。

第二個範例會宣告型別指標清單，請`myList`衍生自`CPtrList`。 儲存清單，並傳回指標`MY_STRUCT`物件。 類別根據`CPtrList`用來儲存不是衍生自物件的指標`CObject`。 `CTypedPtrList` 有許多的型別安全的成員函式： `GetHead`， `GetTail`， `RemoveHead`， `RemoveTail`， `GetNext`， `GetPrev`，和`GetAt`。

###  <a name="_core_typed.2d.pointer_map_usage"></a> 型別指標對應使用方式

型別指標對應類別[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)，採用三個參數：*BASE_CLASS*，*金鑰*，以及*值*。 *BASE_CLASS*參數指定要從中衍生新類別的類別： `CMapPtrToWord`， `CMapPtrToPtr`， `CMapStringToPtr`， `CMapWordToPtr`， `CMapStringToOb`，依此類推。 *索引鍵*相當於*金鑰*在`CMap`:它會指定用於查閱的索引鍵的類型。 *值*相當於*值*在`CMap`:它會指定儲存在 map 中的物件型別。 例如：

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

第一個範例是根據地圖`CMapPtrToPtr`— 它會使用`CString`金鑰對應到指標`MY_STRUCT`。 您可以藉由呼叫型別安全查閱預存指標`Lookup`成員函式。 您可以使用 **[]** 運算子來查詢儲存的指標並將它加入如果找不到。 您可以逐一查看對應使用型別安全和`GetNextAssoc`函式。 您也可以呼叫其他成員函式類別的`CMapPtrToPtr`。

第二個範例是根據地圖`CMapStringToOb`— 它會使用字串索引鍵對應至預存指標`CMyObject`物件。 您可以使用相同的型別安全成員之前的段落中所述，或者您可以呼叫類別的成員`CMapStringToOb`。

> [!NOTE]
>  如果您指定**類別**或是**結構**類型*值*參數，而非指標或參考類型、 類別或結構必須有複製建構函式。

如需詳細資訊，請參閱 <<c0> [ 如何讓類型安全集合](../mfc/how-to-make-a-type-safe-collection.md)。

## <a name="see-also"></a>另請參閱

[集合](../mfc/collections.md)
