---
title: ATL COM 物件的基礎知識
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319562"
---
# <a name="fundamentals-of-atl-com-objects"></a>ATL COM 物件的基礎知識

下圖描述了用於定義 ATL COM 物件的類和介面之間的關係。

![ATL 結構](../atl/media/vc307y1.gif "ATL 結構")

> [!NOTE]
> 此圖顯示`CComObject`派生`CYourClass`自`CComAggObject`而`CComPolyObject`並作為成員`CYourClass`變數包含的函數。

有三種方法可以定義 ATL COM 物件。 標準選項是使用派生自`CComObject``CYourClass`的類。 第二個選項是使用`CComAggObject`類創建聚合物件。 第三個選項是使用`CComPolyObject`類別 。 `CComPolyObject`充當混合體:它可以作為類`CComObject``CComAggObject`或 類運行,具體取決於它最初創建的方式。 有關如何使用類別的詳細資訊,`CComPolyObject`請參考[CComPolyObject 類別](../atl/reference/ccompolyobject-class.md)。

使用標準 ATL COM 時,可以使用兩個物件:外部物件和內部物件。 外部用戶端通過外部物件中定義的包裝函數訪問內部物件的功能。 外部物件的型`CComObject`態為 。

使用聚合物件時,外部物件不為內部物件的功能提供包裝器。 相反,外部物件提供外部用戶端直接訪問的指標。 在這種情況下,外部物件的類型`CComAggObject`為 。 內部物件是外部物件的成員變數,它是類型`CYourClass`。

由於用戶端不必通過外部物件與內部物件交互,因此聚合物件通常效率更高。 此外,外部物件不必知道聚合物件的功能,因為聚合物件的介面直接可供用戶端使用。 但是,並非所有物件都可以聚合。 要聚合物件,需要考慮到聚合來設計它。

ATL 分兩個階段實現[I 未知:](/windows/win32/api/unknwn/nn-unknwn-iunknown)

- [ ](../atl/reference/ccomobject-class.md)CComObject、CComAggObject 或[CComPolyObject](../atl/reference/ccompolyobject-class.md)`IUnknown`實現[CComAggObject](../atl/reference/ccomaggobject-class.md)這些方法。

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md)或[CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md)管理 的`IUnknown`引用計數和外部指標。

ATL COM 物件的其他方面由其他類處理:

- [CComCoClass](../atl/reference/ccomcoclass-class.md)定義物件的預設類工廠和聚合模型。

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供物件上任何`IDispatch Interface`雙 介面部分的默認實現。

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)`ISupportErrorInfo`實現了 確保錯誤資訊可以正確傳播到呼叫鏈上的介面。

## <a name="in-this-section"></a>本節內容

[實作 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
顯示實現`CComObjectRootEx`的 COM 映射項目範例。

[實作 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
討論**\*DECLARE__AGGREGATABLE**巨`CComObject``CComAggObject`集如何影響`CComPolyObject`與的使用 。

[支援 IDispatch 和 IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
列出用於支援和`IDispatch``IErrorInfo`介面的 ATL 實現類。

[支援 IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
討論實現類連接點的步驟。

[變更預設類別與聚合模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
顯示用於更改預設類工廠和聚合模型的宏。

[建立集合物件](../atl/creating-an-aggregated-object.md)<br/>
列出創建聚合物件的步驟。

## <a name="related-sections"></a>相關章節

[建立 ATL 專案](../atl/reference/creating-an-atl-project.md)<br/>
提供有關創建 ATL COM 物件的資訊。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)
