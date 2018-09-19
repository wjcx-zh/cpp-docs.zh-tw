---
title: 屬性和屬性頁類別 (ATL) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.atl.properties
dev_langs:
- C++
helpviewer_keywords:
- property pages, classes
- properties [ATL], classes
- properties [ATL]
ms.assetid: 31616f98-69f8-48b2-8d58-b8e7d1c2b2d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29400fc2e47b419587b81164aa5a7720a7ef134b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065708"
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

