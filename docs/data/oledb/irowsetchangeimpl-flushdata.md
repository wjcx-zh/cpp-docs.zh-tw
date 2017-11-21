---
title: "Irowsetchangeimpl:: Flushdata |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs: C++
helpviewer_keywords: FlushData method
ms.assetid: fd4bc73b-bc25-4aab-90d5-0bed92670c88
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 31555e1f8305a281955902b71fdc71fbcc5405e5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetchangeimplflushdata"></a>IRowsetChangeImpl::FlushData
覆寫此屬性的資料認可至其存放區提供者。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT FlushData(  
   HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush   
);  
```  
  
#### <a name="parameters"></a>參數  
 *hRowToFlush*  
 [in]資料列的控制代碼。 此資料列的類型決定從*RowClass*樣板引數的`IRowsetImpl`類別 (`CSimpleRow`依預設)。  
  
 *hAccessorToFlush*  
 [in]包含繫結資訊以及中的類型資訊的存取子控制代碼其**PROVIDER_MAP** (請參閱[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md))。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>另請參閱  
 [IRowsetChangeImpl 類別](../../data/oledb/irowsetchangeimpl-class.md)