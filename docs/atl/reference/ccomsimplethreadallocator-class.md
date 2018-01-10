---
title: "CComSimpleThreadAllocator 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs: C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 244443692478d0391c2079e55995c1fef1e1655e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator 類別
這個類別會管理類別的執行緒選取`CComAutoThreadModule`。  
  
## <a name="syntax"></a>語法  
  
```
class CComSimpleThreadAllocator
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](#getthread)|選取一個執行緒。|  
  
## <a name="remarks"></a>備註  
 `CComSimpleThreadAllocator`管理執行緒選取項目[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。 `CComSimpleThreadAllocator::GetThread`只要逐一循環顯示每個執行緒，並傳回序列中的下一個。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="getthread"></a>CComSimpleThreadAllocator::GetThread  
 選取一個執行緒藉由指定序列中下一個執行緒。  
  
```
int GetThread(CComApartment* /* pApt */, int nThreads);
```  
  
### <a name="parameters"></a>參數  
 `pApt`  
 不使用 ATL 的預設實作。  
  
 `nThreads`  
 EXE 模組中的執行緒數目上限。  
  
### <a name="return-value"></a>傳回值  
 介於零的整數和 ( `nThreads` -1)。 識別一 EXE 模組中的執行緒。  
  
### <a name="remarks"></a>備註  
 您可以覆寫`GetThread`提供選取不同方法，或請使用`pApt`參數。  
  
 `GetThread`會呼叫[CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)。  
  
## <a name="see-also"></a>請參閱  
 [CComApartment 類別](../../atl/reference/ccomapartment-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
