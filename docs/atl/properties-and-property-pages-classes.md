---
title: 屬性和屬性頁類別 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
ms.openlocfilehash: 05c3a67e278389bb2ab1b07e9d6cf63cbe347c63
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57807517"
---
# <a name="properties-and-property-pages-classes"></a>屬性和屬性頁類別

下列類別支援屬性和屬性頁：

- [CComDispatchDriver](../atl/reference/atl-typedefs.md#ccomdispatchdriver)擷取或設定物件的屬性，透過`IDispatch`指標。

- [CStockPropImpl](../atl/reference/cstockpropimpl-class.md)實作 ATL 支援的內建屬性

- [IPerPropertyBrowsingImpl](../atl/reference/iperpropertybrowsingimpl-class.md)存取物件的屬性頁面中的資訊。

- [IPersistPropertyBagImpl](../atl/reference/ipersistpropertybagimpl-class.md)會將物件的屬性儲存在用戶端提供的屬性包。

- [IPropertyPageImpl](../atl/reference/ipropertypageimpl-class.md)管理特定的屬性頁中的屬性工作表。

- [IPropertyPage2Impl](../atl/reference/ipropertypage2impl-class.md)類似於`IPropertyPageImpl`，但也可讓用戶端屬性頁中選取特定的屬性。

- [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md)取得之物件所支援的屬性頁面的 Clsid。

## <a name="related-articles"></a>相關文章

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)

[ATL COM 屬性頁](../atl/atl-com-property-pages.md)

## <a name="see-also"></a>另請參閱

[類別概觀](../atl/atl-class-overview.md)<br/>
[屬性對應巨集](../atl/reference/property-map-macros.md)
