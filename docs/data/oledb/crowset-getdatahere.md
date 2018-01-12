---
title: "Crowset:: Getdatahere |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset<TAccessor>::GetDataHere
- CRowset<TAccessor>.GetDataHere
- CRowset.GetDataHere
- GetDataHere
- CRowset::GetDataHere
- ATL::CRowset::GetDataHere
- ATL::CRowset<TAccessor>::GetDataHere
- ATL.CRowset<TAccessor>.GetDataHere
- ATL.CRowset.GetDataHere
dev_langs: C++
helpviewer_keywords: GetDataHere method
ms.assetid: 2fe2a987-1c4c-4299-876e-0591caf63af4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7429ec4b451536d3271432d3822de04ecae7dd87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetgetdatahere"></a>CRowset::GetDataHere
從目前資料列擷取資料，並將它放入指定的緩衝區。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT GetDataHere(   
   int nAccessor,   
   void* pBuffer    
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `nAccessor`  
 [in]用來存取資料的存取子的索引編號。  
  
 `pBuffer`  
 [out]將目前記錄資料緩衝區。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 如需如何使用這個函式的範例，請參閱[MultiRead 的範例](../../visual-cpp-samples.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [CRowset::GetData](../../data/oledb/crowset-getdata.md)