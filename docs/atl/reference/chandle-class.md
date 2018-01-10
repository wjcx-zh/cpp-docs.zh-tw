---
title: "CHandle 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs: C++
helpviewer_keywords: CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd58ba8ce15bb26b4e5b768baedbf8ddfe829f2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="chandle-class"></a>CHandle 類別
這個類別會提供建立和使用的控制代碼物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
class CHandle
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|建構函式。|  
|[CHandle:: ~ CHandle](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|呼叫此方法以附加`CHandle`至現有的控制代碼的物件。|  
|[CHandle::Close](#close)|呼叫這個方法來關閉`CHandle`物件。|  
|[CHandle::Detach](#detach)|呼叫此方法以中斷連結的控制代碼從`CHandle`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::operator 控制代碼](#operator_handle)|傳回儲存的控制代碼的值。|  
|[CHandle::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|儲存控制代碼的成員變數。|  
  
## <a name="remarks"></a>備註  
 A`CHandle`需要控制代碼時，就可以使用物件： 其主要差異在於，`CHandle`物件將會自動刪除。  
  
> [!NOTE]
>  某些應用程式開發介面函式將會使用 NULL 的空的或無效的控制代碼，而其他則使用 INVALID_HANDLE_VALUE。 `CHandle`只會使用 NULL，且會將 INVALID_HANDLE_VALUE 視為真正的控制代碼。 如果您呼叫可傳回 INVALID_HANDLE_VALUE API，您應該檢查此值，然後再呼叫[CHandle::Attach](#attach)或將其傳遞至`CHandle`建構函式，並改為傳遞 NULL。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="attach"></a>CHandle::Attach  
 呼叫此方法以附加`CHandle`至現有的控制代碼的物件。  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>參數  
 `h`  
 `CHandle`會取得擁有權的控制代碼`h`。  
  
### <a name="remarks"></a>備註  
 指派`CHandle`物件`h`處理。 對其偵錯組建 ATLASSERT 就會引發如果`h`是 NULL。 不進行任何其他檢查有效性的控制代碼。  
  
##  <a name="chandle"></a>CHandle::CHandle  
 建構函式。  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>參數  
 `h`  
 現有的控制代碼或`CHandle`。  
  
### <a name="remarks"></a>備註  
 建立新`CHandle`物件，您可以選擇使用現有的控制代碼或`CHandle`物件。  
  
##  <a name="dtor"></a>CHandle:: ~ CHandle  
 解構函式。  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放`CHandle`藉由呼叫物件[CHandle::Close](#close)。  
  
##  <a name="close"></a>CHandle::Close  
 呼叫這個方法來關閉`CHandle`物件。  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>備註  
 關閉開啟的物件控制代碼。 如果控制代碼為 NULL，則為則**關閉**已經過呼叫，ATLASSERT 就會引發在偵錯組建。  
  
##  <a name="detach"></a>CHandle::Detach  
 呼叫此方法以中斷連結的控制代碼從`CHandle`物件。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回要卸離的控制代碼。  
  
### <a name="remarks"></a>備註  
 釋放的控制代碼的擁有權。  
  
##  <a name="m_h"></a>CHandle::m_h  
 儲存控制代碼的成員變數。  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>CHandle::operator =  
 指派運算子。  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>參數  
 `h`  
 `CHandle`會取得擁有權的控制代碼`h`。  
  
### <a name="return-value"></a>傳回值  
 傳回新的參考`CHandle`物件。  
  
### <a name="remarks"></a>備註  
 如果`CHandle`物件目前包含的控制代碼，則會關閉。 `CHandle`傳遞中會有其設定為 NULL 的控制代碼參考的物件。 如此可確保兩個`CHandle`物件絕不會包含相同的作用中控制代碼。  
  
##  <a name="operator_handle"></a>CHandle::operator 控制代碼  
 傳回儲存的控制代碼的值。  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回值儲存在[CHandle::m_h](#m_h)。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
