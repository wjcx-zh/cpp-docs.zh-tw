---
title: ATL 集合和列舉程式
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 502bedb1773dc2a6edbd6679d50e9c5946228283
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491893"
---
# <a name="atl-collections-and-enumerators"></a>ATL 集合和列舉程式

`collection`是 COM 物件, 它會提供允許存取資料項目群組 (原始資料或其他物件) 的介面。 遵循提供物件群組存取之標準的介面, 稱為「*集合介面*」。

集合介面至少必須提供一個`Count`屬性, 以傳回集合中的專案數`Item` 、根據索引從集合中傳回專案的屬性, 以及`_NewEnum`傳回的屬性。集合的列舉值。 或者, 集合介面可以提供`Add`和`Remove`方法, 以允許在集合中插入或刪除專案, 以及移除所有專案`Clear`的方法。

`enumerator`是 COM 物件, 它會提供介面來逐一查看集合中的專案。 列舉值介面透過四個必要的方法, 提供對集合元素的序列`Next`存取`Skip`: `Reset`、、 `Clone`和。

您可以藉由讀取參考內容 (例如[IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring)介面) 來深入瞭解列舉值介面。

## <a name="in-this-section"></a>本節內容

[ATL 集合和列舉程式類別](../atl/atl-collection-and-enumerator-classes.md)<br/>
簡要描述並提供可協助您執行集合和枚舉器的 ATL 類別連結。

[集合和列舉程式介面的設計原則](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
討論每種介面類別型背後的不同設計原則。

[實作 C++ 標準程式庫架構集合](../atl/implementing-an-stl-based-collection.md)<br/>
擴充的範例會逐步引導您完成C++標準程式庫型集合的執行。

## <a name="related-sections"></a>相關章節

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

[ATLCollections 範例](../overview/visual-cpp-samples.md)<br/>
示範如何使用`ICollectionOnSTLImpl`和`CComEnumOnSTL`的範例, 以及自訂複製原則類別的執行方式。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)
