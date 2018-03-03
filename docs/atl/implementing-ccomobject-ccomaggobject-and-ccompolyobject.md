---
title: "實作 Ccomobject<、 CComAggObject 和 CComPolyObject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CComPolyObject
- CComAggObject
- CComObject
dev_langs:
- C++
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54f237a629c4af9ea7ae30aeca21c03786abcd97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>實作 Ccomobject<、 CComAggObject 和 CComPolyObject
樣板類別[Ccomobject<](../atl/reference/ccomobject-class.md)， [CComAggObject](../atl/reference/ccomaggobject-class.md)，和[CComPolyObject](../atl/reference/ccompolyobject-class.md)一律會繼承鏈結中最常衍生的類別。 他們要負責處理的方法中的所有**IUnknown**: `QueryInterface`， `AddRef`，和**發行**。 此外，`CComAggObject`和`CComPolyObject`（當用於彙總的物件） 提供特殊的參考計數和`QueryInterface`內部未知所需的語意。  
  
 是否`CComObject`， `CComAggObject`，或`CComPolyObject`用取決於您宣告一個 （或無） 下列巨集：  
  
|巨集|作用|  
|-----------|------------|  
|`DECLARE_NOT_AGGREGATABLE`|一律會使用`CComObject`。|  
|`DECLARE_AGGREGATABLE`|使用`CComAggObject`如果已彙總物件和`CComObject`如果不是。 `CComCoClass`包含此巨集，如果沒有任何**DECLARE_\*_AGGREGATABLE**巨集宣告在類別中，這會是預設值。|  
|`DECLARE_ONLY_AGGREGATABLE`|一律會使用`CComAggObject`。 如果物件不會彙總，則傳回錯誤。|  
|`DECLARE_POLY_AGGREGATABLE`|ATL 建立的執行個體**CComPolyObject\<CYourClass >**時**IClassFactory::CreateInstance**呼叫。 在建立期間，會檢查的外部未知的值。 如果是**NULL**， **IUnknown**實作非彙總的物件。 如果不是外部未知**NULL**， **IUnknown**彙總物件，則實作。|  
  
 使用的優點`CComAggObject`和`CComObject`的實作**IUnknown**最適合用於所建立物件的類型。 比方說，非彙總的物件只需要一個參考計數，而彙總的物件需要內部未知的參考計數和外部未知的指標。  
  
 使用的優點`CComPolyObject`是，您可以避免必須同時`CComAggObject`和`CComObject`處理彙總及非彙總的情況下在模組中。 單一`CComPolyObject`物件會處理這兩種情況。 這表示您可以在模組中存在 vtable 只能有一個複本和一份函式。 如果您的 vtable 很大，這可以大幅降低模組大小。 不過，如果您的 vtable 很小，使用`CComPolyObject`會造成較大的模組大小因為沒有最佳化彙總或非彙總物件，因為`CComAggObject`和`CComObject`。  
  
## <a name="see-also"></a>請參閱  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)   
 [彙總和 Class Factory 巨集](../atl/reference/aggregation-and-class-factory-macros.md)

