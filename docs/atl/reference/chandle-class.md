---
title: "CHandle 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 19
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: bbc0703ae5eaab01c0819be7e378509c7dc579ef
ms.lasthandoff: 02/24/2017

---
# <a name="chandle-class"></a>CHandle 類別
這個類別提供建立和使用控制代碼物件的方法。  
  
## <a name="syntax"></a>語法  
  
```
class CHandle
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|建構函式。|  
|[CHandle:: ~ CHandle](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|呼叫這個方法來附加`CHandle`至現有的控制代碼的物件。|  
|[CHandle::Close](#close)|呼叫這個方法來關閉`CHandle`物件。|  
|[CHandle::Detach](#detach)|呼叫這個方法來卸離的控制代碼從`CHandle`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CHandle::operator 控制代碼](#operator_handle)|傳回儲存的控制代碼值。|  
|[CHandle::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|儲存控制代碼的成員變數。|  
  
## <a name="remarks"></a>備註  
 A`CHandle`需要控制代碼時，就可以使用物件︰ 其主要差異在於，`CHandle`物件將會自動刪除。  
  
> [!NOTE]
>  有些 API 函式將會使用 NULL 的空的或無效的控制代碼，而其他則使用 INVALID_HANDLE_VALUE。 `CHandle`只會使用 NULL，而且會將 INVALID_HANDLE_VALUE 視為真正的控制代碼。 如果您呼叫會傳回 INVALID_HANDLE_VALUE API，您應該檢查此值，然後再呼叫[CHandle::Attach](#attach)或將它傳遞給`CHandle`建構函式，並改為傳遞 NULL。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="attach"></a>CHandle::Attach  
 呼叫這個方法來附加`CHandle`至現有的控制代碼的物件。  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>參數  
 `h`  
 `CHandle`會取得控制代碼的擁有權`h`。  
  
### <a name="remarks"></a>備註  
 指派`CHandle`物件傳遞給`h`處理。 在偵錯組建中 ATLASSERT，將產生`h`是 NULL。 控制代碼的有效性的任何其他檢查不撤銷狀態。  
  
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
 建立新`CHandle`物件時，您可以選擇使用現有的控制代碼或`CHandle`物件。  
  
##  <a name="dtor"></a>CHandle:: ~ CHandle  
 解構函式。  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>備註  
 釋出`CHandle`物件呼叫[CHandle::Close](#close)。  
  
##  <a name="close"></a>CHandle::Close  
 呼叫這個方法來關閉`CHandle`物件。  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>備註  
 關閉開啟的物件控制代碼。 如果控制代碼為 NULL，而如果**關閉**已經過呼叫，ATLASSERT，系統將產生在偵錯組建。  
  
##  <a name="detach"></a>CHandle::Detach  
 呼叫這個方法來卸離的控制代碼從`CHandle`物件。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回要卸離的控制代碼。  
  
### <a name="remarks"></a>備註  
 釋放控制代碼的擁有權。  
  
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
 `CHandle`會取得控制代碼的擁有權`h`。  
  
### <a name="return-value"></a>傳回值  
 傳回新的參考`CHandle`物件。  
  
### <a name="remarks"></a>備註  
 如果`CHandle`物件目前包含的控制代碼，則會關閉。 `CHandle`傳入必須設為 NULL 的控制代碼參考的物件。 這可確保兩個`CHandle`物件絕不會包含相同的作用中控制代碼。  
  
##  <a name="operator_handle"></a>CHandle::operator 控制代碼  
 傳回儲存的控制代碼值。  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回值儲存在[CHandle::m_h](#m_h)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

