---
title: "CComObjectRoot 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31295a07704e272799398aa82c6a9f0bbac17717
ms.openlocfilehash: 34653d55091a8e872f075010a0ef7cecbb3484c8
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ccomobjectroot-class"></a>CComObjectRoot 類別
此 typedef 的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)根據執行緒模型的伺服器預設值。  
  
## <a name="syntax"></a>語法  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## <a name="remarks"></a>備註  
 `CComObjectRoot`是`typedef`的[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)可以在預設的執行緒模型的伺服器。 因此[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)參考任何[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)。  
  
 `CComObjectRootEx`處理非彙總及彙總物件的物件參考計數管理。 如果您的物件不會被彙總，而且存放的外部未知的指標，如果您的物件正在彙總，它會保留物件參考計數。 對於彙總的物件，`CComObjectRootEx`方法可用來處理失敗，內部物件的建構，而且要保護以防止內部介面發行時刪除外部物件或內部的物件已刪除。  
  
## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  
  
## <a name="see-also"></a>另請參閱  
 [CComObjectRootEx 類別成員](http://msdn.microsoft.com/en-us/e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx 類別](../../atl/reference/ccomobjectrootex-class.md)   
 [CComAggObject 類別](../../atl/reference/ccomaggobject-class.md)   
 [CComObject 類別](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject 類別](../../atl/reference/ccompolyobject-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

