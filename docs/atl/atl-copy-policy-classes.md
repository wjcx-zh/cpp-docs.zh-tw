---
title: ATL 複製原則類別
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317385"
---
# <a name="atl-copy-policy-classes"></a>ATL 複製原則類別

複製策略類別是用於初始化、複製與移除資料的[實用程式類別](../atl/utility-classes.md)。 複製策略類允許您為任何類型的數據定義複製語義,並定義不同數據類型之間的轉換。

ATL 在其實用以下樣本時使用複製策略類別:

- [CComEnumimpl](../atl/reference/ccomenumimpl-class.md)

- [伊納姆翁斯特萊普](../atl/reference/ienumonstlimpl-class.md)

- [ICollectiononSTLimpl](../atl/reference/icollectiononstlimpl-class.md)

通過封裝複製或轉換數據所需的資訊,這些數據可以作為範本參數傳遞,ATL 開發人員提供了這些類的極端可重用性。 例如,如果需要使用任何任意數據類型實現集合,則只需提供相應的複製策略;如果需要使用任意數據類型實現集合,則只需適當的複製策略。您永遠不必觸摸實現集合的代碼。

## <a name="definition"></a>定義

根據定義,提供以下靜態函數的類別是複製策略類:

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

您可以將類型`DestinationType`和*SourceType*取代為每個複製策略的任意資料類型。

> [!NOTE]
> 儘管可以為任何任意數據類型定義複製策略類,但在 ATL 代碼中使用類應限制有意義的類型。 例如,在將複製策略類與 ATL 的集合或枚舉器實現一起使用`DestinationType`時, 必須是一種類型,可以在 COM 介面方法中用作參數。

使用**init**初始化資料、**複製**以複製數據以及**銷毀**以釋放數據。 初始化、複製和銷毀的確切含義是複製策略類的域,並且會根據所涉及的數據類型而變化。

關於複製策略類的使用和實現有兩個要求:

- 要**複製**的第一個參數只能接收指向以前使用**init**初始化的數據的指標。

- **銷毀**必須只接收指向以前使用**init**或通過**複製**複製的數據的指標。

## <a name="standard-implementations"></a>標準實現

ATL`_Copy`以`_CopyInterface`與 樣本類別提供兩個複製策略類別:

- 這個`_Copy`類別複製(資料類型) 之間不轉換,因為它只提供一個樣本參數來指定與`DestinationType` *SourceType*。 此範本的通用實現不包含初始化或銷毀代碼,並用於`memcpy`複製數據。 ATL 還提供 VARIANT、LPOLESTR、OLEVERB 和 CONNECTDATA 數據類型的`_Copy`專業化認證。

- 類`_CopyInterface`提供了一個實現,用於按照標準 COM 規則複製介面指標。 同樣,此類只允許同質複製,因此它使用簡單的賦值和調用`AddRef`來執行複製。

## <a name="custom-implementations"></a>自訂實作

通常,您需要為異構複製(即資料類型之間的轉換)定義自己的複製策略類。 有關自定義複製策略類的一些範例,請查看[ATLCollections](../overview/visual-cpp-samples.md)範例中VCUE_Copy.h和 VCUE_CopyString.h 的檔。 這些檔包含兩個範本複製策略類,`GenericCopy``MapCopy`以及 ,以及針對不同數據`GenericCopy`類型的多種專門化。

### <a name="genericcopy"></a>通用複製

`GenericCopy`允許您指定*SourceType*`DestinationType`並作為 範本參數。 以下是 VCUE_Copy.h 類別的`GenericCopy`最通用 形式:

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h 還包含此類的以下專門化`GenericCopy<BSTR>`: `GenericCopy<VARIANT, BSTR>` `GenericCopy<BSTR, VARIANT>` , . VCUE_CopyString.h 包含用於從**std:字串**s`GenericCopy<std::string>`複製`GenericCopy<VARIANT, std::string>`的`GenericCopy<BSTR, std::string>`專門 化 : 與 。 您可以通過提供您`GenericCopy`自己的 進一步專業化來增強。

### <a name="mapcopy"></a>地圖複製

`MapCopy`假定要複製的數據存儲在C++標準庫樣式映射中,因此允許您指定存儲數據的地圖類型和目標類型。 類的實現只是使用*MapType*類提供的 typedefs 來確定源數據類型`GenericCopy`並調用相應的 類。 不需要此類的專業化化。

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>另請參閱

[實現基於C++標準庫集合](../atl/implementing-an-stl-based-collection.md)<br/>
[ATL集合範例](../overview/visual-cpp-samples.md)
