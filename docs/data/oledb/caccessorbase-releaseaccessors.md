---
title: "Caccessorbase:: Releaseaccessors |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
dev_langs: C++
helpviewer_keywords: ReleaseAccessors method
ms.assetid: f08bc88e-0552-4a9c-9c65-b4061094649a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 313231e2c53a1e5afc409dd85b430d5029914b1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="caccessorbasereleaseaccessors"></a>CAccessorBase::ReleaseAccessors
釋放類別建立的存取子。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT ReleaseAccessors(  
   IUnknown* pUnk   
);  
```  
  
#### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown** COM 物件已建立存取子的介面。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 從呼叫[caccessorrowset:: Close](../../data/oledb/caccessorrowset-close.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CAccessorBase 類別](../../data/oledb/caccessorbase-class.md)