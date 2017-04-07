---
title: "CComGITPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 9fe9d9f6d03a6d72c1ce3332419c738570a53803
ms.lasthandoff: 02/24/2017

---
# <a name="ccomgitptr-class"></a>CComGITPtr 類別
這個類別提供方法來處理介面指標和全域介面表 (GIT)。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要儲存在 GIT 中的介面指標的類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|建構函式。|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|呼叫這個方法，以在全域介面表 (GIT) 中註冊的介面指標。|  
|[CComGITPtr::CopyTo](#copyto)|呼叫這個方法，以將介面由全域介面資料表 (GIT) 複製到傳入的指標。|  
|[CComGITPtr::Detach](#detach)|呼叫這個方法來取消關聯的介面從`CComGITPtr`物件。|  
|[CComGITPtr::GetCookie](#getcookie)|呼叫這個方法，傳回從 cookie`CComGITPtr`物件。|  
|[CComGITPtr::Revoke](#revoke)|呼叫這個方法來移除全域介面表 (GIT) 的介面。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|傳回從 cookie`CComGITPtr`物件。|  
|[CComGITPtr::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Cookie。|  
  
## <a name="remarks"></a>備註  
 彙總無限制執行緒封送處理器，而且需要使用從其他物件中取得的介面指標的物件必須採取額外步驟，以確保介面會正確地封送處理。 這通常涉及儲存在 GIT 中的介面指標，而從 GIT 每次使用時取得的指標。 類別`CComGITPtr`提供可協助您使用儲存在 GIT 中的介面指標。  
  
> [!NOTE]
>  只有 dcom 1.1 版的 Windows 95 和更新版本，Windows 98、 Windows NT 4.0 Service Pack 3 及更新版本和 Windows 2000 上，您可以使用全域介面資料表設備。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="attach"></a>CComGITPtr::Attach  
 呼叫這個方法，以在全域介面表 (GIT) 中註冊的介面指標。  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>參數  
 `p`  
 要加入至 GIT 的介面指標。  
  
 `dwCookie`  
 Cookie，用來識別的介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，GIT 不正確，或者 cookie 等於 NULL，將會發生判斷錯誤。  
  
##  <a name="ccomgitptr"></a>CComGITPtr::CComGITPtr  
 建構函式。  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>參數  
 [in] `p`  
 介面指標儲存在全域介面表 (GIT)。  
  
 [in] `git`  
 若要將現有的參考`CComGITPtr`物件。  
  
 [in] `dwCookie`  
 Cookie，用來識別的介面指標。  
  
 [in] `rv`  
 來源`CComGITPtr`移動的資料物件。  
  
### <a name="remarks"></a>備註  
 建立新`CComGITPtr`物件時，您可以選擇使用現有`CComGITPtr`物件。  
  
 建構函式利用`rv`是移動建構函式。 將資料從來源移`rv`，然後`rv`已清除。  
  
##  <a name="dtor"></a>CComGITPtr:: ~ CComGITPtr  
 解構函式。  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>備註  
 移除介面由全域介面資料表 (GIT)，使用[CComGITPtr::Revoke](#revoke)。  
  
##  <a name="copyto"></a>CComGITPtr::CopyTo  
 呼叫這個方法，以將介面由全域介面資料表 (GIT) 複製到傳入的指標。  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 也就是接收的介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 從 GIT 介面會複製到傳入的指標。 當不再需要時，必須由呼叫端釋放指標。  
  
##  <a name="detach"></a>CComGITPtr::Detach  
 呼叫這個方法來取消關聯的介面從`CComGITPtr`物件。  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回從 cookie`CComGITPtr`物件。  
  
### <a name="remarks"></a>備註  
 移除介面 GIT，從呼叫端決定是否使用[CComGITPtr::Revoke](#revoke)。  
  
##  <a name="getcookie"></a>CComGITPtr::GetCookie  
 呼叫這個方法，傳回從 cookie`CComGITPtr`物件。  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 cookie。  
  
### <a name="remarks"></a>備註  
 Cookie 是用來識別介面，以及其位置的變數。  
  
##  <a name="m_dwcookie"></a>CComGITPtr::m_dwCookie  
 Cookie。  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>備註  
 Cookie 是用來識別介面，以及其位置的成員變數。  
  
##  <a name="operator_eq"></a>CComGITPtr::operator =  
 指派運算子。  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>參數  
 [in] `p`  
 介面的指標。  
  
 [in] `git`  
 對 `CComGITPtr` 物件的參考。  
  
 [in] `dwCookie`  
 Cookie，用來識別的介面指標。  
  
 [in] `rv`  
 `CComGITPtr`移動的資料。  
  
### <a name="return-value"></a>傳回值  
 傳回更新`CComGITPtr`物件。  
  
### <a name="remarks"></a>備註  
 新值指派給`CComGITPtr`從現有的物件或從全域介面資料表參考的物件。  
  
##  <a name="operator_dword"></a>CComGITPtr::operator DWORD  
 相關聯的 cookie 傳回`CComGITPtr`物件。  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>備註  
 Cookie 是用來識別介面，以及其位置的變數。  
  
##  <a name="revoke"></a>CComGITPtr::Revoke  
 呼叫此方法以移除目前的介面由全域介面資料表 (GIT)。  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 移除介面從 GIT。  
  
## <a name="see-also"></a>另請參閱  
 [無限制執行緒封送處理器](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [跨 Apartment 存取介面](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [使用全域介面資料表的時機](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [類別概觀](../../atl/atl-class-overview.md)

