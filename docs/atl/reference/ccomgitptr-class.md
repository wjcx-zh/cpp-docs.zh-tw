---
title: CComGITPtr 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: bf509d027833610e4251c009d4e444dad3fdd5ce
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296029"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 類別

這個類別提供方法來處理介面指標和全域介面表 (GIT)。

## <a name="syntax"></a>語法

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>參數

*T*<br/>
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
|[CComGITPtr::Attach](#attach)|呼叫這個方法來註冊全域介面表 (GIT) 的介面指標。|
|[CComGITPtr::CopyTo](#copyto)|呼叫這個方法來複製全域介面表 (GIT) 中的介面，以傳遞的指標。|
|[CComGITPtr::Detach](#detach)|呼叫這個方法來取消關聯的介面`CComGITPtr`物件。|
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
|[CComGITPtr::m_dwCookie](#m_dwcookie)|在 cookie 中。|

## <a name="remarks"></a>備註

彙總無限制執行緒封送處理器，而且需要使用從其他物件中取得的介面指標的物件必須採取額外步驟以確保介面會正確地封送處理。 通常這牽涉到儲存在 GIT 中的介面指標，是每次從 GIT 取得滑鼠指標。 此類別`CComGITPtr`可協助您使用儲存在 GIT 中的介面指標。

> [!NOTE]
>  只有使用 dcom 1.1 版的 Windows 95 和更新版本、 Windows 98、 Windows NT 4.0 Service Pack 3 和更新版本和 Windows 2000 上全域介面表功能。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="attach"></a>  CComGITPtr::Attach

呼叫這個方法來註冊全域介面表 (GIT) 的介面指標。

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
要加入至 GIT 的介面指標。

*dwCookie*<br/>
用來識別的介面指標的 cookie。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

在偵錯組建，或如果 GIT 不是有效的如果 cookie 是等於 NULL，會發生判斷提示錯誤。

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

*p*<br/>
[in]若要儲存在全域介面表 (GIT) 介面指標。

*git*<br/>
[in]若要將現有的參考`CComGITPtr`物件。

*dwCookie*<br/>
[in]Cookie，用來識別的介面指標。

*rv*<br/>
[in]來源`CComGITPtr`移動的資料物件。

### <a name="remarks"></a>備註

建立新`CComGITPtr`物件，或者使用 現有`CComGITPtr`物件。

建構函式利用*rv*是移動建構函式。 將資料從來源移*rv*，然後*rv*已清除。

##  <a name="dtor"></a>  CComGITPtr:: ~ CComGITPtr

解構函式。

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>備註

介面移除全域介面表 (GIT)，使用[CComGITPtr::Revoke](#revoke)。

##  <a name="copyto"></a>  CComGITPtr::CopyTo

呼叫這個方法來複製全域介面表 (GIT) 中的介面，以傳遞的指標。

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>參數

*pp*<br/>
也就是接收的介面指標。

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

從 GIT 介面會複製到傳入的指標。 當不再需要時，指標必須釋放由呼叫端。

##  <a name="detach"></a>  CComGITPtr::Detach

呼叫這個方法來取消關聯的介面`CComGITPtr`物件。

```
DWORD Detach() throw();
```

### <a name="return-value"></a>傳回值

傳回從 cookie`CComGITPtr`物件。

### <a name="remarks"></a>備註

它是由要移除介面從 GIT，呼叫者使用[CComGITPtr::Revoke](#revoke)。

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

在 cookie 中。

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

*p*<br/>
[in]介面的指標。

*git*<br/>
[in]參考`CComGITPtr`物件。

*dwCookie*<br/>
[in]Cookie，用來識別的介面指標。

*rv*<br/>
[in]`CComGITPtr`移動資料。

### <a name="return-value"></a>傳回值

傳回已更新`CComGITPtr`物件。

### <a name="remarks"></a>備註

指派新值到`CComGITPtr`從現有的物件，或從全域介面表參考的物件。

##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD

傳回具有相關聯的 cookie`CComGITPtr`物件。

```
operator DWORD() const;
```

### <a name="remarks"></a>備註

Cookie 是用來識別介面和其位置的變數。

##  <a name="revoke"></a>  CComGITPtr::Revoke

呼叫這個方法來移除全域介面表 (GIT) 目前的介面。

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>傳回值

會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。

### <a name="remarks"></a>備註

從 GIT 中移除介面。

## <a name="see-also"></a>另請參閱

[無限制執行緒封送處理器](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[存取在 Apartment 之間的介面](/windows/desktop/com/accessing-interfaces-across-apartments)<br/>
[使用全域介面資料表的時機](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[類別概觀](../../atl/atl-class-overview.md)
