---
title: CComGITPtr 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 049873ce6ff630e8f00ea5ad5ec9b3786bd5e71b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363622"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 類別
這個類別會提供處理介面指標的方法和全域介面表 (GIT)。  
  
## <a name="syntax"></a>語法  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 要儲存在 GIT 中的介面指標的類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|建構函式。|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|呼叫此方法以在全域介面表 (GIT) 中註冊的介面指標。|  
|[CComGITPtr::CopyTo](#copyto)|呼叫此方法以將介面從全域介面表 (GIT) 複製到傳入的指標。|  
|[CComGITPtr::Detach](#detach)|呼叫這個方法來取消關聯的介面，從`CComGITPtr`物件。|  
|[CComGITPtr::GetCookie](#getcookie)|呼叫此方法以傳回從 cookie`CComGITPtr`物件。|  
|[CComGITPtr::Revoke](#revoke)|呼叫這個方法來移除全域介面表 (GIT) 的介面。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|傳回從 cookie`CComGITPtr`物件。|  
|[CComGITPtr::operator =](#operator_eq)|指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Cookie。|  
  
## <a name="remarks"></a>備註  
 彙總無限制執行緒封送處理器，且需要使用取自其他物件的介面指標的物件必須採取額外步驟以確保介面會正確地封送處理。 通常這項作業包括將介面指標儲存在 GIT 從 GIT 每次使用時取得的指標。 類別`CComGITPtr`提供可協助您使用儲存在 GIT 中的介面指標。  
  
> [!NOTE]
>  只有使用 dcom 1.1 版的 Windows 95 和更新版本、 Windows 98、 Windows NT 4.0 Service Pack 3 和更新版本，以及 Windows 2000 上的全域介面資料表設備。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  
##  <a name="attach"></a>  CComGITPtr::Attach  
 呼叫此方法以在全域介面表 (GIT) 中註冊的介面指標。  
  
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
 在偵錯組建中，如果 GIT 無效，或如果 cookie 等於 NULL，會發生判斷提示錯誤。  
  
##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr  
 建構函式。  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `p`  
 要儲存在全域介面表 (GIT) 介面指標。  
  
 [輸入] `git`  
 若要將現有的參考`CComGITPtr`物件。  
  
 [輸入] `dwCookie`  
 此 cookie 會用來識別的介面指標。  
  
 [輸入] `rv`  
 來源`CComGITPtr`可以移動資料的物件。  
  
### <a name="remarks"></a>備註  
 建立新`CComGITPtr`物件，您可以選擇使用現有`CComGITPtr`物件。  
  
 建構函式使用`rv`是移動建構函式。 將資料從來源移`rv`，然後`rv`已清除。  
  
##  <a name="dtor"></a>  CComGITPtr:: ~ CComGITPtr  
 解構函式。  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>備註  
 介面移除全域介面表 (GIT)，使用[CComGITPtr::Revoke](#revoke)。  
  
##  <a name="copyto"></a>  CComGITPtr::CopyTo  
 呼叫此方法以將介面從全域介面表 (GIT) 複製到傳入的指標。  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pp`  
 也就是接收的介面指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 從 GIT 介面會複製到傳入的指標。 已不再需要時，必須由呼叫端釋放指標。  
  
##  <a name="detach"></a>  CComGITPtr::Detach  
 呼叫這個方法來取消關聯的介面，從`CComGITPtr`物件。  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回從 cookie`CComGITPtr`物件。  
  
### <a name="remarks"></a>備註  
 若要移除介面從 GIT，呼叫端負責決定是否使用[CComGITPtr::Revoke](#revoke)。  
  
##  <a name="getcookie"></a>  CComGITPtr::GetCookie  
 呼叫此方法以傳回從 cookie`CComGITPtr`物件。  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的 cookie。  
  
### <a name="remarks"></a>備註  
 Cookie 是用來識別介面和其位置的變數。  
  
##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie  
 Cookie。  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>備註  
 Cookie 是用來識別介面和其位置的成員變數。  
  
##  <a name="operator_eq"></a>  CComGITPtr::operator =  
 指派運算子。  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `p`  
 介面的指標。  
  
 [輸入] `git`  
 對 `CComGITPtr` 物件的參考。  
  
 [輸入] `dwCookie`  
 此 cookie 會用來識別的介面指標。  
  
 [輸入] `rv`  
 `CComGITPtr`移動的資料。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新`CComGITPtr`物件。  
  
### <a name="remarks"></a>備註  
 指派新值`CComGITPtr`物件、 從現有的物件或從全域介面資料表的參考。  
  
##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD  
 傳回與相關聯的 cookie`CComGITPtr`物件。  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>備註  
 Cookie 是用來識別介面和其位置的變數。  
  
##  <a name="revoke"></a>  CComGITPtr::Revoke  
 呼叫此方法以從全域介面表 (GIT) 中移除目前的介面。  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 從 GIT 中移除介面。  
  
## <a name="see-also"></a>另請參閱  
 [無限制執行緒封送處理器](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [存取在 Apartment 之間的介面](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [使用全域介面資料表的時機](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [類別概觀](../../atl/atl-class-overview.md)
