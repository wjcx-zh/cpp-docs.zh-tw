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
ms.openlocfilehash: 24d81506f1518f980576899a4a104bbfdc0a1438
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296341"
---
# <a name="atl-copy-policy-classes"></a>ATL 複製原則類別

複製原則類別是[公用程式類別](../atl/utility-classes.md)用來初始化、 複製和刪除資料。 複製原則類別可讓您定義的任何類型的資料，複製語意，並定義不同的資料類型之間的轉換。

ATL 用法複製原則類別在其實作中的下列範本：

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

藉由將封裝複製或轉換可以作為範本引數傳遞的複製原則類別中的資料所需的資訊，ATL 開發者提供極大的重複使用這些類別。 例如，如果您需要實作使用任何任意的資料類型的集合，您只需要提供是適當的複製原則;您永遠不必碰觸實作集合的程式碼。

## <a name="definition"></a>定義

根據定義，這個類別提供下列的靜態函式是複製原則類別：

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

您可以取代類型`DestinationType`並*SourceType*複本的每個原則的任意資料類型。

> [!NOTE]
>  雖然您可以定義任何任意的資料類型的複製原則類別，使用 ATL 程式碼中的類別應該限制有意義的類型。 例如，當使用複製原則類別與 ATL 的集合或列舉值實作`DestinationType`必須是可用來當做 COM 介面方法中的參數類型。

使用**init**初始化資料，**複製**若要複製資料，並**終結**釋放資料。 初始化的確切意義、 複製和解構複製原則類別的網域和相關的資料類型會有所不同。

有兩項需求的使用和複製原則類別的實作：

- 第一個參數**複製**必須只會收到您先前已初始化使用的資料指標**init**。

- **終結**必須只會接收您先前已初始化使用的資料指標**init**或透過複製**複製**。

## <a name="standard-implementations"></a>標準的實作

ATL 提供兩個複製原則類別的形式`_Copy`和`_CopyInterface`範本類別：

- `_Copy`類別可讓同質只複製 （不轉換資料類型之間） 因為它只會提供單一範本參數同時指定`DestinationType`並*SourceType*。 此範本的一般實作包含未初始化或解構的程式碼，並使用`memcpy`來複製資料。 ATL 也提供的特製化`_Copy`VARIANT、 LPOLESTR、 OLEVERB 和 CONNECTDATA 資料類型。

- `_CopyInterface`類別會提供複製下列標準的 COM 規則的介面指標的實作。 一次一次這個類別可讓只複製，因此它會使用簡單的設定，以及呼叫`AddRef`來執行複製。

## <a name="custom-implementations"></a>自訂實作

一般而言，您必須定義您自己的複製原則類別，針對異質的複製 （也就是資料類型之間的轉換）。 如需自訂複製原則類別的一些範例，查看 VCUE_Copy.h 和 VCUE_CopyString.h 中的檔案[ATLCollections](../visual-cpp-samples.md)範例。 這些檔案包含兩個範本複製原則類別，`GenericCopy`並`MapCopy`，再加上幾個的特製化的`GenericCopy`不同資料類型。

### <a name="genericcopy"></a>GenericCopy

`GenericCopy` 可讓您指定*SourceType*和`DestinationType`當做樣板引數。 以下是最常見的形式`GenericCopy`VCUE_Copy.h 類別：

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h 也包含此類別的下列特製化： `GenericCopy<BSTR>`， `GenericCopy<VARIANT, BSTR>`， `GenericCopy<BSTR, VARIANT>`。 VCUE_CopyString.h 包含從複製的特製化**std:: string**s `GenericCopy<std::string>`， `GenericCopy<VARIANT, std::string>`，和`GenericCopy<BSTR, std::string>`。 您可以增強`GenericCopy`進一步提供您自己的特製化。

### <a name="mapcopy"></a>MapCopy

`MapCopy` 假設正在複製的資料儲存到 c + + 標準程式庫-style 對應，讓它可讓您指定的對應中的資料儲存和目的地輸入類型。 類別的實作只會使用所提供的 typedef *MapType*類別來判斷來源資料的型別，並呼叫適當`GenericCopy`類別。 此類別的任何特製化所不需。

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>另請參閱

[實作 C++ 標準程式庫架構集合](../atl/implementing-an-stl-based-collection.md)<br/>
[ATLCollections 範例](../visual-cpp-samples.md)
