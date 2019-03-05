---
title: ATL 集合和列舉程式
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 690fc023b72b2606efc190aceb7c266a35a4ebb4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283044"
---
# <a name="atl-collections-and-enumerators"></a>ATL 集合和列舉程式

A`collection`是 COM 物件，提供的介面，可讓您存取一組資料的項目 （未經處理資料或其他物件）。 遵循標準，提供一組物件的存取權就所謂的介面*集合介面*。

集合介面必須提供最少`Count`屬性，可在集合中，傳回的項目數`Item`傳回的項目根據索引，集合中的屬性和`_NewEnum`傳回的屬性集合的列舉值。 或者，可以提供集合介面`Add`並`Remove`方法，以允許要插入或刪除，從集合的項目和`Clear`方法來移除所有項目。

`enumerator`是 COM 物件，逐一查看集合中的項目提供的介面。 列舉程式介面提供序列存取透過四個必要的方法集合的項目： `Next`， `Skip`， `Reset`，和`Clone`。

您可以了解詳細資訊，請閱讀的列舉程式介面參考內容，例如[IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring)介面。

## <a name="in-this-section"></a>本節內容

[ATL 集合和列舉程式類別](../atl/atl-collection-and-enumerator-classes.md)<br/>
簡短描述，並提供連結至 ATL 類別，可協助您實作集合和列舉程式。

[集合和列舉程式介面的設計原則](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
討論每一種介面背後的不同的設計原則。

[實作 C++ 標準程式庫架構集合](../atl/implementing-an-stl-based-collection.md)<br/>
擴充的範例，逐步引導您實作的 c + + 標準程式庫為基礎的集合。

## <a name="related-sections"></a>相關章節

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

[ATLCollections 範例](../visual-cpp-samples.md)<br/>
示範如何使用範例`ICollectionOnSTLImpl`和`CComEnumOnSTL`，以及自訂複製原則類別的實作。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)
