---
title: "CComObjectRoot 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs: C++
helpviewer_keywords: CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2dc617eeb58594262ea272a0a4ef7da2865b73f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 類別
此 typedef 的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)執行緒模型的伺服器預設值根據。  
  
## <a name="syntax"></a>語法  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## <a name="remarks"></a>備註  
 `CComObjectRoot`是`typedef`的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)根據 預設的執行緒模型的伺服器。 因此[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)參考任何[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 `CComObjectRootEx`處理非彙總與彙總物件的物件參考計數管理。 如果您的物件不會被彙總，而且存放的外部未知的指標，如果您的物件進行彙總，它會保留物件參考計數。 對於彙總物件，`CComObjectRootEx`方法可以用來處理失敗，內部物件的建構，並刪除保護以防止刪除內部介面發行時在外部物件或內部的物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  
  
## <a name="see-also"></a>另請參閱  
 [CComObjectRootEx 類別成員](http://msdn.microsoft.com/en-us/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [Ccomobject< 類別](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
