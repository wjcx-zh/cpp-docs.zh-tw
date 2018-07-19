---
title: CHandle 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd962e32f423baba6cfabb90f1d9f7fa5d69e170
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880228"
---
# <a name="chandle-class"></a>CHandle 類別
這個類別提供建立及使用控制代碼物件的方法。  
  
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
|[CHandle::Attach](#attach)|呼叫這個方法來附加`CHandle`至現有的控制代碼的物件。|  
|[CHandle::Close](#close)|呼叫這個方法來關閉`CHandle`物件。|  
|[CHandle::Detach](#detach)|呼叫此方法以中斷連結的控制代碼從`CHandle`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::operator 控制代碼](#operator_handle)|傳回預存的控制代碼的值。|  
|[CHandle::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|儲存的控制代碼的成員變數。|  
  
## <a name="remarks"></a>備註  
 A`CHandle`每當需要控制代碼時，就可以使用物件： 主要差異在於`CHandle`物件會自動刪除。  
  
> [!NOTE]
>  某些 API 函數將 NULL 做為空白或無效的控制代碼，而其他則使用 INVALID_HANDLE_VALUE。 `CHandle` 只會使用 NULL，而且會視為真正的控制代碼的 INVALID_HANDLE_VALUE。 如果您呼叫可傳回 INVALID_HANDLE_VALUE API 時，您應該檢查此值，然後再呼叫[CHandle::Attach](#attach)或將其傳遞至`CHandle`建構函式，並改為傳遞 NULL。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="attach"></a>  CHandle::Attach  
 呼叫這個方法來附加`CHandle`至現有的控制代碼的物件。  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>參數  
 *h*  
 `CHandle` 需要的控制代碼的擁有權*h*。  
  
### <a name="remarks"></a>備註  
 指派`CHandle`物件至*h*處理。 在對其偵錯組建中，ATLASSERT 如果就會引發*h*是 NULL。 控制代碼的有效性的任何其他檢查不撤銷狀態。  
  
##  <a name="chandle"></a>  CHandle::CHandle  
 建構函式。  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>參數  
 *h*  
 現有的控制代碼或`CHandle`。  
  
### <a name="remarks"></a>備註  
 建立新`CHandle`物件，選擇性地使用現有的控制代碼或`CHandle`物件。  
  
##  <a name="dtor"></a>  CHandle:: ~ CHandle  
 解構函式。  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>備註  
 釋放`CHandle`藉由呼叫物件[CHandle::Close](#close)。  
  
##  <a name="close"></a>  CHandle::Close  
 呼叫這個方法來關閉`CHandle`物件。  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>備註  
 關閉開啟的物件控制代碼。 如果控制代碼就是 NULL，則是`Close`已經被呼叫，ATLASSERT 就會引發在偵錯組建。  
  
##  <a name="detach"></a>  CHandle::Detach  
 呼叫此方法以中斷連結的控制代碼從`CHandle`物件。  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回要卸離的控制代碼。  
  
### <a name="remarks"></a>備註  
 釋放的控制代碼的擁有權。  
  
##  <a name="m_h"></a>  CHandle::m_h  
 儲存的控制代碼的成員變數。  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>  CHandle::operator =  
 指派運算子。  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>參數  
 *h*  
 `CHandle` 需要的控制代碼的擁有權*h*。  
  
### <a name="return-value"></a>傳回值  
 傳回新的參考`CHandle`物件。  
  
### <a name="remarks"></a>備註  
 如果`CHandle`物件目前包含的控制代碼，因此將會關閉。 `CHandle`物件傳入必須設為 NULL 的控制代碼參考。 這可確保兩個`CHandle`物件絕不會包含相同的作用中控制代碼。  
  
##  <a name="operator_handle"></a>  CHandle::operator 控制代碼  
 傳回預存的控制代碼的值。  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>備註  
 傳回值儲存在[CHandle::m_h](#m_h)。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
