---
title: "Irowsetchangeimpl:: Setdata |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
dev_langs: C++
helpviewer_keywords: SetData method
ms.assetid: 81e1dd0a-0518-440c-8808-cee76e4929c7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d42f64575e515b67d296acbd21411bcd184d479c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetchangeimplsetdata"></a>IRowsetChangeImpl::SetData
設定一或多個資料行中的資料值。  
  
## <a name="syntax"></a>語法  
  
```  
  
      STDMETHOD ( SetData )(  
   HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData   
);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[irowsetchange:: Setdata](https://msdn.microsoft.com/en-us/library/ms721232.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetChangeImpl 類別](../../data/oledb/irowsetchangeimpl-class.md)