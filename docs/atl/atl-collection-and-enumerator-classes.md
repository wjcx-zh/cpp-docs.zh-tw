---
title: "ATL 集合和列舉值類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerators, ATL classes
- collection classes, ATL
ms.assetid: 6818db73-7094-48d8-a0ca-18147beec362
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b172c0d3a6f453ec0d5f7b5bb3584ebf2f5140e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="atl-collection-and-enumerator-classes"></a>ATL 集合和列舉值類別
ATL 提供下列類別，以協助您實作集合和列舉程式。  
  
|類別|描述|  
|-----------|-----------------|  
|[ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)|集合介面實作|  
|[IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)|列舉值的介面實作 （假設資料儲存在 c + + 標準程式庫相容容器）|  
|[CComEnumImpl](../atl/reference/ccomenumimpl-class.md)|列舉值的介面實作 （假設陣列中儲存的資料）|  
|[CComEnumOnSTL](../atl/reference/ccomenumonstl-class.md)|列舉值物件實作 (使用`IEnumOnSTLImpl`)|  
|[CComEnum](../atl/reference/ccomenum-class.md)|列舉值物件實作 (使用`CComEnumImpl`)|  
|[_Copy](../atl/atl-copy-policy-classes.md)|複製原則類別|  
|[_CopyInterface](../atl/atl-copy-policy-classes.md)|複製原則類別|  
|[CAdapt](../atl/reference/cadapt-class.md)|配接器類別 (隱藏**運算子 （& s)**允許`CComPtr`， `CComQIPtr`，和`CComBSTR`儲存在 c + + 標準程式庫容器)|  
  
## <a name="see-also"></a>請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)

