---
title: "樣板架構類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2beb417bdedab6196ff6d27a387c4b61f083c4ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="template-based-classes"></a>樣板架構類別
本文說明 MFC 3.0 版和更新版本中的型別安全樣板型集合類別。 使用這些範本來建立類型安全集合，會比較方便，有助於比使用非根據樣板的集合類別更有效地提供類型安全。  
  
 MFC 預先定義了兩種類別的範本為基礎的集合：  
  
-   [簡單陣列、 清單和對應類別](#_core_using_simple_array.2c_.list.2c_.and_map_templates)  
  
     `CArray`, `CList`, `CMap`  
  
-   [陣列、 清單和對應的具類型指標](#_core_using_typed.2d.pointer_collection_templates)  
  
     `CTypedPtrArray`, `CTypedPtrList`, `CTypedPtrMap`  
  
 簡單集合類別衍生自類別`CObject`，因此它們在繼承序列化、 動態建立，以及其他屬性的`CObject`。 具類型的指標集合類別會要求您指定此類別衍生自-它必須是其中一個預先定義的 mfc，例如非範本指標集合`CPtrList`或`CPtrArray`。 新的集合類別繼承自指定的基底類別，並使用新的類別成員函式來強制執行型別安全封裝的呼叫基底類別成員。  
  
 如需 c + + 範本的詳細資訊，請參閱[範本](../cpp/templates-cpp.md)中*c + + 語言參考*。  
  
##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a>使用簡單陣列、 清單和對應的範本  
 若要使用的簡單集合範本，您需要知道這些集合中可以儲存的資料種類，以及要在集合宣告中使用何種參數。  
  
###  <a name="_core_simple_array_and_list_usage"></a>簡單陣列和清單的使用方式  
 簡單陣列和清單類別[CArray](../mfc/reference/carray-class.md)和[CList](../mfc/reference/clist-class.md)，採用兩個參數：*類型*和`ARG_TYPE`。 這些類別可以儲存任何資料類型，您在中指定*類型*參數：  
  
-   基本的 c + + 資料類型，例如`int`， `char`，和**float**  
  
-   C + + 結構和類別  
  
-   您定義其他類型  
  
 為了方便和效率，您可以使用`ARG_TYPE`指定函式引數的型別參數。 一般而言，您指定`ARG_TYPE`您在名為的類型，參考*類型*參數。 例如:   
  
 [!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]  
  
 第一個範例會宣告陣列集合中， `myArray`，其中包含`int`s。 第二個範例會宣告清單集合， `myList`，其中存放`CPerson`物件。 集合類別的特定成員函式接受引數所指定的型別`ARG_TYPE`樣板參數。 例如，**新增**類別成員函式`CArray`採用`ARG_TYPE`引數：  
  
 [!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]  
  
###  <a name="_core_simple_map_usage"></a>簡單的對應使用方式  
 簡單的對應類別[CMap](../mfc/reference/cmap-class.md)，採用四個參數：*金鑰*， `ARG_KEY`，*值*，和`ARG_VALUE`。 陣列和清單類別一樣，對應類別可以儲存任何資料類型。 不同於陣列和清單編製索引和排序其儲存的資料，maps 關聯索引鍵和值： 存取儲存在對應中所指定的值相關聯的索引鍵的值。 *金鑰*參數會指定用來存取資料儲存在 map 中的索引鍵的資料類型。 如果類型*金鑰*結構或類別，`ARG_KEY`參數通常是在指定之類型的參考*金鑰*。 *值*參數會指定儲存在 map 中的項目類型。 如果類型`ARG_VALUE`結構或類別，`ARG_VALUE`參數通常是在指定之類型的參考*值*。 例如:   
  
 [!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]  
  
 第一個範例存放區`MY_STRUCT`值，則這兩者存取`int`金鑰，以及存取傳回`MY_STRUCT`所參考的項目。 第二個範例存放區`CPerson`值，則這兩者存取`CString`鍵，並傳回存取項目的參考。 此範例中，可能代表簡單的通訊錄，在其中您查閱的人員姓氏。  
  
 因為*金鑰*參數的類型是`CString`和*KEY_TYPE*參數的類型是`LPCSTR`，做為項目類型的對應中儲存索引鍵`CString`但中參考函式，如`SetAt`透過指標類型的`LPCSTR`。 例如:   
  
 [!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]  
  
##  <a name="_core_using_typed.2d.pointer_collection_templates"></a>使用範本型別指標集合  
 若要使用的型別指標集合範本，您需要知道這些集合中可以儲存的資料種類，以及要在集合宣告中使用何種參數。  
  
###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a>型別指標陣列和清單的使用方式  
 型別指標陣列和清單類別[CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)和[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)，採用兩個參數：`BASE_CLASS`和*類型*。 這些類別可以儲存任何資料類型，您在中指定*類型*參數。 它們衍生自其中一個儲存的指標; 非樣板集合類別指定此基底類別中的`BASE_CLASS`。 對於陣列，使用`CObArray`或`CPtrArray`。 清單，請使用 `CObList`或`CPtrList`。  
  
 作用中，當您宣告為基礎的集合，說出`CObList`，新的類別不只會繼承其基底類別的成員，但它也會宣告許多其他的型別安全成員函式和運算子可協助提供型別安全性封裝呼叫基底類別成員。 這些封裝，管理所有的必要類型轉換。 例如:   
  
 [!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]  
  
 第一個範例會宣告的型別指標陣列， `myArray`、 衍生自`CObArray`。 儲存陣列，並傳回指標`CPerson`物件 (其中`CPerson`類別衍生自`CObject`)。 您可以呼叫任何`CObArray`成員函式，或者您可以呼叫新的型別安全`GetAt`和`ElementAt`函式，或使用型別安全**[]**運算子。  
  
 第二個範例會宣告型別指標的清單中， `myList`、 衍生自`CPtrList`。 清單會儲存並傳回指標`MY_STRUCT`物件。 類別，根據`CPtrList`用來儲存物件不是衍生自指標`CObject`。 `CTypedPtrList`類型安全的成員函式數目： `GetHead`， `GetTail`， `RemoveHead`， `RemoveTail`， `GetNext`， `GetPrev`，和`GetAt`。  
  
###  <a name="_core_typed.2d.pointer_map_usage"></a>型別指標對應的用法  
 型別指標對應類別[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)，採用三個參數： `BASE_CLASS`，*金鑰*，和*值*。 `BASE_CLASS`參數會指定要從中衍生新類別的類別： `CMapPtrToWord`， `CMapPtrToPtr`， `CMapStringToPtr`， `CMapWordToPtr`， `CMapStringToOb`，依此類推。 *索引鍵*類似於*金鑰*中`CMap`： 它會指定用於查閱的索引鍵的類型。 *值*類似於*值*中`CMap`： 它會指定儲存在 map 中的物件類型。 例如:   
  
 [!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]  
  
 第一個範例是根據地圖**CMapPtrToPt**r，它會使用`CString`金鑰對應到指標`MY_STRUCT`。 您可以藉由呼叫安全類型查閱儲存指標`Lookup`成員函式。 您可以使用**[]**運算子來查詢儲存的指標，將它加入如果找不到。 您可以重複使用型別安全的對應和`GetNextAssoc`函式。 您也可以呼叫其他成員函式的類別`CMapPtrToPtr`。  
  
 第二個範例是根據地圖**CMapStringToO**b，它會使用字串索引鍵對應至預存的指標`CMyObject`物件。 您可以使用相同的型別安全成員之前的段落中所述，或者您可以呼叫類別的成員`CMapStringToOb`。  
  
> [!NOTE]
>  如果您指定**類別**或`struct`輸入*值*參數，而非指標或參考類型、 類別或結構必須具有複製建構函式。  
  
 如需詳細資訊，請參閱[如何製作類型安全集合](../mfc/how-to-make-a-type-safe-collection.md)。  
  
## <a name="see-also"></a>請參閱  
 [集合](../mfc/collections.md)

