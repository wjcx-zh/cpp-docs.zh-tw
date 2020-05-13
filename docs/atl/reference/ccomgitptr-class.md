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
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327831"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 類別

此類提供了處理介面指標和全域介面表 (GIT) 的方法。

## <a name="syntax"></a>語法

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>參數

*T*<br/>
要存儲在 GIT 中的介面指標的類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComGITPtr:CComGITPtr](#ccomgitptr)|建構函式。|
|[CComGITPtr:*CComGITPtr](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComGITPtr::附加](#attach)|調用此方法以在全域介面表 (GIT) 中註冊介面指標。|
|[CComGITPtr:: 複製到](#copyto)|呼叫此方法以將介面從全域介面表 (GIT) 複製到傳遞的指標。|
|[CComGITPtr::D埃塔奇](#detach)|調用此方法以取消介面與`CComGITPtr`對象的關聯。|
|[CComGITPtr:取得餅乾](#getcookie)|調用此方法以從`CComGITPtr`物件返回 Cookie。|
|[CComGITPtr:撤銷](#revoke)|呼叫此方法從全域介面表 (GIT) 中刪除介面。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CComGITPtr::操作員DWORD](#operator_dword)|從`CComGITPtr`物件返回 Cookie。|
|[CComGITPtr::運算符 |](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CComGITPtr:m_dwCookie](#m_dwcookie)|餅乾|

## <a name="remarks"></a>備註

聚合自由線程封送器且需要使用從其他對象獲取的介面指標的物件必須採取額外步驟,以確保介面正確封送。 這通常涉及將介面指標存儲在 GIT 中,並在每次使用時從 GIT 獲取指標。 提供該`CComGITPtr`類是為了説明您使用存儲在 GIT 中的介面指標。

> [!NOTE]
> 全域介面表功能僅在 Windows 95 上提供 DCOM 版本 1.1 及更高版本、Windows 98、Windows NT 4.0 和 Service Pack 3 及更高版本。Windows 2000。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr::附加

調用此方法以在全域介面表 (GIT) 中註冊介面指標。

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>參數

*P*<br/>
要添加到 GIT 的介面指標。

*dwCookie*<br/>
用於標識介面指標的 Cookie。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

在除錯產生中,如果 GIT 無效,或者如果 Cookie 等於 NULL,則會發生斷言錯誤。

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr:CComGITPtr

建構函式。

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>參數

*P*<br/>
[在]要存儲在全域介面表 (GIT) 中的介面指標。

*Git*<br/>
[在]對現有`CComGITPtr`物件的引用。

*dwCookie*<br/>
[在]用於標識介面指標的 Cookie。

*Rv*<br/>
[在]要從`CComGITPtr`中移動數據的源物件。

### <a name="remarks"></a>備註

創建新`CComGITPtr`物件,可以選擇使用`CComGITPtr`現有 物件。

使用*rv*的構造函數是移動構造函數。 數據從源*rv*移動,然後*清除 rv。*

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr:*CComGITPtr

解構函式。

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>備註

使用[CComGITPtr:::revoke](#revoke),從全域介面表 (GIT) 中刪除介面。

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr:: 複製到

呼叫此方法以將介面從全域介面表 (GIT) 複製到傳遞的指標。

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>參數

*Pp*<br/>
接收介面的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

從 GIT 的介面複製到傳遞的指標。 當不再需要指標時,調用方必須釋放該指標。

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr::D埃塔奇

調用此方法以取消介面與`CComGITPtr`對象的關聯。

```
DWORD Detach() throw();
```

### <a name="return-value"></a>傳回值

從`CComGITPtr`物件返回 Cookie。

### <a name="remarks"></a>備註

呼叫者使用[CComGITPtr:::revoke,](#revoke)由呼叫方從 GIT 中刪除介面。

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr:取得餅乾

調用此方法以從`CComGITPtr`物件返回 Cookie。

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>傳回值

返回 Cookie。

### <a name="remarks"></a>備註

Cookie 是用於標識介面及其位置的變數。

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr:m_dwCookie

餅乾

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>備註

Cookie 是用於標識介面及其位置的成員變數。

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr::運算符 |

分配運算符。

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>參數

*P*<br/>
[在]指向介面的指標。

*Git*<br/>
[在]對物件的參考`CComGITPtr`。

*dwCookie*<br/>
[在]用於標識介面指標的 Cookie。

*Rv*<br/>
[在]`CComGITPtr`要移動數據。

### <a name="return-value"></a>傳回值

返回更新`CComGITPtr`的物件。

### <a name="remarks"></a>備註

從現有`CComGITPtr`物件或從引用到全域介面表向物件分配新值。

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr::操作員DWORD

返回與`CComGITPtr`物件關聯的 Cookie。

```
operator DWORD() const;
```

### <a name="remarks"></a>備註

Cookie 是用於標識介面及其位置的變數。

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr:撤銷

呼叫此方法從全域介面表 (GIT) 中刪除當前介面。

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

從 GIT 中刪除介面。

## <a name="see-also"></a>另請參閱

[自由螺紋封送器](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[跨公寓存取介面](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[何時使用全域介面表](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[類別概觀](../../atl/atl-class-overview.md)
