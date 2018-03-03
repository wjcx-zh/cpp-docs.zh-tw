---
title: "ATL 集合和列舉程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52b74f51733947ca46c0ddb1039f92ce7f69e670
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collections-and-enumerators"></a>ATL 集合和列舉程式
A`collection`是 COM 物件，提供的介面，可讓您存取資料項 （原始資料或其他物件） 的群組。 一種介面，依循標準提供一組物件的存取權就所謂的*集合介面*。  
  
 集合介面必須至少提供**計數**屬性，傳回集合中的項目數**項目**屬性集合為基礎的索引，從傳回的項目，並`_NewEnum`傳回集合的列舉值的屬性。 或者，可以提供的集合介面**新增**和**移除**方法，以允許要插入或刪除集合中，從項目和**清除**方法移除所有的項目。  
  
 `enumerator`是 COM 物件，提供介面，用於逐一查看集合中的項目。 列舉程式介面提供序列存取透過四個必要的方法集合的項目： `Next`，**略過**，**重設**，和`Clone`。  
  
 您可以進一步了解列舉程式介面所了解典型 （但完全虛數） [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)介面。  
  
## <a name="in-this-section"></a>本節內容  
 [ATL 集合和列舉程式類別](../atl/atl-collection-and-enumerator-classes.md)  
 簡短描述，並提供連結至 ATL 類別，可協助您實作的集合和列舉程式。  
  
 [集合和列舉程式介面的設計原則](../atl/design-principles-for-collection-and-enumerator-interfaces.md)  
 討論不同的設計背後的原則每一種介面。  
  
 [實作 C++ 標準程式庫架構集合](../atl/implementing-an-stl-based-collection.md)  
 擴充的範例會引導您進行實作的 c + + 標準程式庫為基礎的集合。  
  
## <a name="related-sections"></a>相關章節  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。  
  
 [ATLCollections 範例](../visual-cpp-samples.md)  
 示範如何使用範例`ICollectionOnSTLImpl`和`CComEnumOnSTL`，以及自訂複製原則類別的實作。  
  
## <a name="see-also"></a>請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)

