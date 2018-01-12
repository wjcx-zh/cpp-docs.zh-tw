---
title: "Idbinitializeimpl:: M_dwstatus |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
dev_langs: C++
helpviewer_keywords: m_dwStatus
ms.assetid: 7621ccff-ca60-4b75-9c6a-c104bd0e2038
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 360eeb936e2bf7b4219e9e6dc8eb95fe40c52c6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="idbinitializeimplmdwstatus"></a>IDBInitializeImpl::m_dwStatus
資料來源的旗標。  
  
## <a name="syntax"></a>語法  
  
```  
  
DWORD m_dwStatus;  
  
```  
  
## <a name="remarks"></a>備註  
 這些旗標會指定，或表示為資料來源物件的各種屬性的狀態。 包含一或多個項目`enum`值：  
  
```  
enum DATASOURCE_FLAGS {  
    DSF_MASK_INIT     = 0xFFFFF00F,  
    DSF_PERSIST_DIRTY = 0x00000001,  
    DSF_INITIALIZED   = 0x00000010,  
};  
```  
  
|||  
|-|-|  
|**DSF_MASK_INIT**|若要啟用的未初始化的狀態還原遮罩。|  
|**DSF_PERSIST_DIRTY**|如果資料來源物件需要持續性 （亦即，如果已變更）。|  
|**DSF_INITIALIZED**|如果在初始化資料來源，設定。|  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h  
  
## <a name="see-also"></a>請參閱  
 [IDBInitializeImpl 類別](../../data/oledb/idbinitializeimpl-class.md)   
 [Idbinitializeimpl:: Idbinitializeimpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)   
 [IDBInitializeImpl::Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)