---
title: CComSafeDeleteCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821645"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 類別

這個類別會提供方法來取得和釋放重要區段物件的擁有權。

## <a name="syntax"></a>語法

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|建構函式。|
|[CComSafeDeleteCriticalSection：： ~ CComSafeDeleteCriticalSection](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|Name|描述|
|----------|-----------------|
|[CComSafeDeleteCriticalSection：： Init](#init)|建立並初始化重要區段物件。|
|[CComSafeDeleteCriticalSection：： Lock](#lock)|取得重要區段物件的擁有權。|
|[CComSafeDeleteCriticalSection：： Term](#term)|釋放 critical 區段物件所使用的系統資源。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bInitialized](#m_binitialized)|旗標內部 `CRITICAL_SECTION` 物件是否已初始化。|

## <a name="remarks"></a>備註

`CComSafeDeleteCriticalSection` 衍生自類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 不過，`CComSafeDeleteCriticalSection` 透過[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)提供額外的安全機制。

當 `CComSafeDeleteCriticalSection` 的實例超出範圍或從記憶體中明確刪除時，會自動清除基礎重要區段物件（如果仍然有效）。 此外，如果基礎重要區段物件尚未配置或已從記憶體釋放， [CComSafeDeleteCriticalSection：： Term](#term)方法將會正常結束。

如需重要區段協助程式類別的詳細資訊，請參閱[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>需求

**標頭：** atlcore。h

##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

建構函式。

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>備註

將[m_bInitialized](#m_binitialized)的資料成員設定為 FALSE。

##  <a name="dtor"></a>CComSafeDeleteCriticalSection：： ~ CComSafeDeleteCriticalSection

解構函式。

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>備註

如果[m_bInitialized](#m_binitialized)資料成員設定為 TRUE，則釋放記憶體中的內部 `CRITICAL_SECTION` 物件。

##  <a name="init"></a>CComSafeDeleteCriticalSection：： Init

呼叫[Init](/visualstudio/debugger/init)的基類執行，並在成功時將[M_BINITIALIZED](#m_binitialized)設定為 TRUE。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

傳回[CComCriticalSection：： Init](../../atl/reference/ccomcriticalsection-class.md#init)的結果。

##  <a name="lock"></a>CComSafeDeleteCriticalSection：： Lock

呼叫[鎖定](ccomcriticalsection-class.md#lock)的基類實作為。

```
HRESULT Lock();
```

### <a name="return-value"></a>傳回值

傳回[CComCriticalSection：： Lock](../../atl/reference/ccomcriticalsection-class.md#lock)的結果。

### <a name="remarks"></a>備註

這個方法會假設在進入時， [m_bInitialized](#m_binitialized)資料成員設為 TRUE。 如果不符合此條件，則會在 Debug 組建中產生判斷提示。

如需函式行為的詳細資訊，請參閱[CComCriticalSection：： Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。

##  <a name="m_binitialized"></a>CComSafeDeleteCriticalSection：： m_bInitialized

旗標內部 `CRITICAL_SECTION` 物件是否已初始化。

```
bool m_bInitialized;
```

### <a name="remarks"></a>備註

`m_bInitialized` 資料成員是用來追蹤與[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)類別相關聯之基礎 `CRITICAL_SECTION` 物件的有效性。 如果未將此旗標設定為 TRUE，則不會嘗試從記憶體釋放基礎 `CRITICAL_SECTION` 物件。

##  <a name="term"></a>CComSafeDeleteCriticalSection：： Term

如果內部 `CRITICAL_SECTION` 物件有效，則呼叫[CComCriticalSection：： Term](../../atl/reference/ccomcriticalsection-class.md#term)的基類實。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

傳回[CComCriticalSection：： Term](../../atl/reference/ccomcriticalsection-class.md#term)的結果，如果[m_bInitialized](#m_binitialized)在進入時設定為 FALSE，則傳回 S_OK。

### <a name="remarks"></a>備註

即使內部 `CRITICAL_SECTION` 物件無效，也可以安全地呼叫這個方法。 如果[m_bInitialized](#m_binitialized)資料成員設定為 TRUE，這個類別的析構函式就會呼叫這個方法。

## <a name="see-also"></a>請參閱

[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
