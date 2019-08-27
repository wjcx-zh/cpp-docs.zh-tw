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
ms.openlocfilehash: 00265cc445191a5a539ab21d6f64b255849495e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497270"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 類別

這個類別會提供處理介面指標和全域介面表 (GIT) 的方法。

## <a name="syntax"></a>語法

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>參數

*T*<br/>
要儲存在 GIT 中之介面指標的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|建構函式。|
|[CComGITPtr:: ~ CComGITPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|呼叫這個方法, 在全域介面表 (GIT) 中註冊介面指標。|
|[CComGITPtr::CopyTo](#copyto)|呼叫這個方法, 將介面從全域介面表 (GIT) 複製到傳遞的指標。|
|[CComGITPtr::Detach](#detach)|呼叫這個方法, 將介面`CComGITPtr`與物件取消關聯。|
|[CComGITPtr::GetCookie](#getcookie)|呼叫這個方法, 以從`CComGITPtr`物件傳回 cookie。|
|[CComGITPtr::Revoke](#revoke)|呼叫這個方法, 從全域介面表 (GIT) 中移除介面。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComGITPtr:: operator DWORD](#operator_dword)|從`CComGITPtr`物件傳回 cookie。|
|[CComGITPtr:: operator =](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Cookie。|

## <a name="remarks"></a>備註

匯總無限制執行緒封送處理器並需要使用從其他物件取得之介面指標的物件, 必須採取額外的步驟, 以確保介面已正確封送處理。 通常這牽涉到將介面指標儲存在 GIT 中, 並在每次使用時從 GIT 取得指標。 提供的`CComGITPtr`類別可協助您使用儲存在 GIT 中的介面指標。

> [!NOTE]
>  全域介面表設施僅適用于具有 DCOM 1.1 版和更新版本、Windows 98、Windows NT 4.0 (含 Service Pack 3 和更新版本) 和 Windows 2000 的 Windows 95。

## <a name="requirements"></a>需求

**標頭:** atlbase.h。h

##  <a name="attach"></a>CComGITPtr:: Attach

呼叫這個方法, 在全域介面表 (GIT) 中註冊介面指標。

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>參數

*p*<br/>
要加入至 GIT 的介面指標。

*dwCookie*<br/>
用來識別介面指標的 cookie。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

在「偵錯工具組建」中, 如果 GIT 無效, 或 cookie 等於 Null, 就會發生判斷提示錯誤。

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

*p*<br/>
在要儲存在全域介面表 (GIT) 中的介面指標。

*git*<br/>
在現有`CComGITPtr`物件的參考。

*dwCookie*<br/>
在用來識別介面指標的 cookie。

*rv*<br/>
在要移動`CComGITPtr`資料的來源物件。

### <a name="remarks"></a>備註

建立新`CComGITPtr`的物件, 並選擇性地使用`CComGITPtr`現有的物件。

使用*rv*的函式是移動的函式。 資料會從來源 ( *rv*) 移動, 然後清除*rv* 。

##  <a name="dtor"></a>CComGITPtr:: ~ CComGITPtr

解構函式。

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>備註

使用[CComGITPtr:: Revoke](#revoke), 從全域介面表 (GIT) 中移除介面。

##  <a name="copyto"></a>CComGITPtr:: CopyTo

呼叫這個方法, 將介面從全域介面表 (GIT) 複製到傳遞的指標。

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>參數

*pp*<br/>
要接收介面的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

從 GIT 將介面複製到傳遞的指標。 當不再需要指標時, 呼叫端必須釋放它。

##  <a name="detach"></a>CComGITPtr::D etach

呼叫這個方法, 將介面`CComGITPtr`與物件取消關聯。

```
DWORD Detach() throw();
```

### <a name="return-value"></a>傳回值

從`CComGITPtr`物件傳回 cookie。

### <a name="remarks"></a>備註

呼叫者會使用[CComGITPtr:: Revoke](#revoke), 從 GIT 移除介面。

##  <a name="getcookie"></a>CComGITPtr:: System.windows.application.getcookie

呼叫這個方法, 以從`CComGITPtr`物件傳回 cookie。

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>傳回值

傳回 cookie。

### <a name="remarks"></a>備註

Cookie 是用來識別介面和其位置的變數。

##  <a name="m_dwcookie"></a>CComGITPtr::m_dwCookie

Cookie。

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>備註

Cookie 是用來識別介面和其位置的成員變數。

##  <a name="operator_eq"></a>CComGITPtr:: operator =

指派運算子。

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>參數

*p*<br/>
在介面的指標。

*git*<br/>
在`CComGITPtr`物件的參考。

*dwCookie*<br/>
在用來識別介面指標的 cookie。

*rv*<br/>
在要`CComGITPtr`移動資料的來源。

### <a name="return-value"></a>傳回值

傳回已更新`CComGITPtr`的物件。

### <a name="remarks"></a>備註

從現有的物件或全域`CComGITPtr`介面資料表的參考, 將新值指派給物件。

##  <a name="operator_dword"></a>CComGITPtr:: operator DWORD

傳回與`CComGITPtr`物件相關聯的 cookie。

```
operator DWORD() const;
```

### <a name="remarks"></a>備註

Cookie 是用來識別介面和其位置的變數。

##  <a name="revoke"></a>CComGITPtr:: Revoke

呼叫這個方法, 從全域介面表 (GIT) 中移除目前的介面。

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

從 GIT 移除介面。

## <a name="see-also"></a>另請參閱

[無限制執行緒封送處理器](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[跨公寓存取介面](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[使用全域介面資料表的時機](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[類別總覽](../../atl/atl-class-overview.md)
