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
ms.openlocfilehash: 115cbd466f51db271f4be65ce708fe54c7f2b2ce
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833630"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection 類別

此類別提供取得和釋放重要區段物件之擁有權的方法。

## <a name="syntax"></a>語法

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComSafeDeleteCriticalSection：： CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|建構函式。|
|[CComSafeDeleteCriticalSection：： ~ CComSafeDeleteCriticalSection](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComSafeDeleteCriticalSection：： Init](#init)|建立並初始化重要區段物件。|
|[CComSafeDeleteCriticalSection：： Lock](#lock)|取得重要區段物件的擁有權。|
|[CComSafeDeleteCriticalSection：： Term](#term)|釋放重要區段物件所使用的系統資源。|

### <a name="data-members"></a>資料成員

|資料成員|描述|
|-|-|
|[m_bInitialized](#m_binitialized)|旗標內建物件是否已 `CRITICAL_SECTION` 初始化。|

## <a name="remarks"></a>備註

`CComSafeDeleteCriticalSection` 衍生自類別 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 但是，透過 `CComSafeDeleteCriticalSection` [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)提供額外的安全性機制。

當的實例 `CComSafeDeleteCriticalSection` 超出範圍，或從記憶體中明確地刪除時，會自動清除基礎重要區段物件（如果仍然有效）。 此外，如果基礎重要區段物件尚未配置或已從記憶體釋放， [CComSafeDeleteCriticalSection：： Term](#term) 方法將會正常結束。

如需重要區段 helper 類別的詳細資訊，請參閱 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>規格需求

**標頭：** atlcore。h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a> CComSafeDeleteCriticalSection：： CComSafeDeleteCriticalSection

建構函式。

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>備註

將 [m_bInitialized](#m_binitialized) 的資料成員設為 FALSE。

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a> CComSafeDeleteCriticalSection：： ~ CComSafeDeleteCriticalSection

解構函式。

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>備註

`CRITICAL_SECTION`如果[m_bInitialized](#m_binitialized)資料成員設為 TRUE，則從記憶體釋放內建物件。

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a> CComSafeDeleteCriticalSection：： Init

如果成功，則呼叫 [Init](/visualstudio/debugger/init) 的基底類別執行，並將 [M_BINITIALIZED](#m_binitialized) 設定為 TRUE。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

傳回 [CComCriticalSection：： Init](../../atl/reference/ccomcriticalsection-class.md#init)的結果。

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a> CComSafeDeleteCriticalSection：： Lock

呼叫 [鎖定](ccomcriticalsection-class.md#lock)的基底類別實作為。

```
HRESULT Lock();
```

### <a name="return-value"></a>傳回值

傳回 [CComCriticalSection：： Lock](../../atl/reference/ccomcriticalsection-class.md#lock)的結果。

### <a name="remarks"></a>備註

當輸入時，此方法會假設 [m_bInitialized](#m_binitialized) 資料成員設為 TRUE。 如果不符合此條件，就會在偵錯工具組建中產生判斷提示。

如需函數行為的詳細資訊，請參閱 [CComCriticalSection：： Lock](../../atl/reference/ccomcriticalsection-class.md#lock)。

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a> CComSafeDeleteCriticalSection：： m_bInitialized

旗標內建物件是否已 `CRITICAL_SECTION` 初始化。

```
bool m_bInitialized;
```

### <a name="remarks"></a>備註

`m_bInitialized`資料成員是用來追蹤 `CRITICAL_SECTION` 與[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)類別相關聯之基礎物件的有效性。 `CRITICAL_SECTION`如果此旗標未設定為 TRUE，則不會嘗試從記憶體釋放基礎物件。

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a> CComSafeDeleteCriticalSection：： Term

如果內建物件有效，則呼叫 [CComCriticalSection：： Term](../../atl/reference/ccomcriticalsection-class.md#term) 的基類實作為基底類別 `CRITICAL_SECTION` 。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

傳回 [CComCriticalSection：： Term](../../atl/reference/ccomcriticalsection-class.md#term)的結果，如果在進入時將 [M_BINITIALIZED](#m_binitialized) 設為 FALSE，則傳回 S_OK。

### <a name="remarks"></a>備註

即使內建物件無效，也可以安全地呼叫這個方法 `CRITICAL_SECTION` 。 如果 [m_bInitialized](#m_binitialized) 資料成員設為 TRUE，則這個類別的函式會呼叫這個方法。

## <a name="see-also"></a>另請參閱

[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
