---
title: CComSafe 移除關鍵部份類別
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
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327374"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafe 移除關鍵部份類別

此類提供了獲取和釋放關鍵節物件的擁有權的方法。

## <a name="syntax"></a>語法

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComSafe 刪除關鍵部份::CcomSafe刪除關鍵部分](#ccomsafedeletecriticalsection)|建構函式。|
|[CComSafe 刪除關鍵部份::_CcomSafe刪除關鍵部分](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComSafe 刪除關鍵部份::Init](#init)|創建並初始化關鍵截面物件。|
|[CComSafe 移除關鍵部份:鎖定](#lock)|獲取關鍵部分物件的擁有權。|
|[CComSafe 刪除關鍵部份::術語](#term)|釋放關鍵部分物件使用的系統資源。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bInitialized](#m_binitialized)|標記內部`CRITICAL_SECTION`物件是否已初始化。|

## <a name="remarks"></a>備註

`CComSafeDeleteCriticalSection`衍生式[CCom 臨界節](../../atl/reference/ccomcriticalsection-class.md)。 然而,`CComSafeDeleteCriticalSection`透過[CCom 臨界部分](../../atl/reference/ccomcriticalsection-class.md)提供了額外的安全機制。

當實例`CComSafeDeleteCriticalSection`超出範圍或從記憶體中顯式刪除時,如果基礎關鍵部分物件仍然有效,則會自動清理該物件。 此外,如果基礎關鍵節物件尚未分配或已經從記憶體中釋放[,CComSafeDelete關鍵節:術語](#term)方法將正常退出。

有關關鍵部分幫助器類的詳細資訊,請參閱[CCom 臨界節](../../atl/reference/ccomcriticalsection-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CCom 臨界部分](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafe 刪除關鍵部份::CcomSafe刪除關鍵部分

建構函式。

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>備註

將[m_bInitialized](#m_binitialized)資料成員設置為 FALSE。

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafe 刪除關鍵部份::_CcomSafe刪除關鍵部分

解構函式。

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>備註

如果m_bInitialized資料`CRITICAL_SECTION`成員設置為[m_bInitialized](#m_binitialized)TRUE, 則從記憶體中釋放內部物件。

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafe 刪除關鍵部份::Init

調用[Init](/visualstudio/debugger/init)的基類實現,如果成功[,m_bInitialized](#m_binitialized)將設置為 TRUE。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

傳[回 CCom 臨界節的結果::Init](../../atl/reference/ccomcriticalsection-class.md#init)。

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafe 移除關鍵部份:鎖定

調用[Lock](ccomcriticalsection-class.md#lock)的基類實現。

```
HRESULT Lock();
```

### <a name="return-value"></a>傳回值

傳[回 CCom 臨界節的結果:鎖定](../../atl/reference/ccomcriticalsection-class.md#lock)。

### <a name="remarks"></a>備註

此方法假定[m_bInitialized](#m_binitialized)資料成員在輸入時設置為 TRUE。 如果未滿足此條件,則在調試生成中生成斷言。

有關函數行為的詳細資訊,請參閱[CCom臨界節::鎖定](../../atl/reference/ccomcriticalsection-class.md#lock)。

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafe 刪除關鍵部份::m_bInitialized

標記內部`CRITICAL_SECTION`物件是否已初始化。

```
bool m_bInitialized;
```

### <a name="remarks"></a>備註

數據`m_bInitialized`成員用於追蹤與`CRITICAL_SECTION`[CComSafeDelete 關鍵節](../../atl/reference/ccomsafedeletecriticalsection-class.md)類關聯的基礎物件的有效性。 如果未將此`CRITICAL_SECTION`標誌設置為 TRUE,則不會嘗試從記憶體中釋放基礎物件。

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafe 刪除關鍵部份::術語

調用[CCom臨界節的基本類實現::](../../atl/reference/ccomcriticalsection-class.md#term)`CRITICAL_SECTION`如果內部 物件有效,則術語。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

返回[CCom臨界節的結果::術語](../../atl/reference/ccomcriticalsection-class.md#term),或者S_OK如果[m_bInitialized](#m_binitialized)在輸入時設置為 FALSE。

### <a name="remarks"></a>備註

即使內部`CRITICAL_SECTION`物件無效,也是安全的調用此方法。 如果[m_bInitialized](#m_binitialized)資料成員設置為 TRUE,則此類的析構函數將調用此方法。

## <a name="see-also"></a>另請參閱

[CCom臨界節類](../../atl/reference/ccomcriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
