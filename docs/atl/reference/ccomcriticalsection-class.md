---
title: CCom臨界節類
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: f3991d217fbc201bd428ed2522a5c4c25e074928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327973"
---
# <a name="ccomcriticalsection-class"></a>CCom臨界節類

此類提供了獲取和釋放關鍵節物件的擁有權的方法。

## <a name="syntax"></a>語法

```
class CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCom臨界部分:Ccom臨界節](#ccomcriticalsection)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom臨界部分::Init](#init)|創建並初始化關鍵截面物件。|
|[CCom臨界部分:鎖](#lock)|獲取關鍵部分物件的擁有權。|
|[CCom臨界部分::學期](#term)|釋放關鍵部分物件使用的系統資源。|
|[CCom臨界部分:解鎖](#unlock)|釋放關鍵部分物件的擁有權。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCom臨界部分:m_sec](#m_sec)|物件CRITICAL_SECTION。|

## <a name="remarks"></a>備註

`CComCriticalSection`類似於[CComAuto 臨界節](../../atl/reference/ccomautocriticalsection-class.md)類,只不過您必須顯式初始化和釋放關鍵部分。

通常,您可以`CComCriticalSection`通過**類型def**名稱[「臨界節](ccommultithreadmodel-class.md#criticalsection)」使用。 此名稱引用`CComCriticalSection`時,使用[CComMultiThreadModel。](../../atl/reference/ccommultithreadmodel-class.md)

有關使用此類比直接呼叫`Lock``Unlock`更安全的方法,請參閱[CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md)。

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="ccomcriticalsectionccomcriticalsection"></a><a name="ccomcriticalsection"></a>CCom臨界部分:Ccom臨界節

建構函式。

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>備註

將[m_sec](#m_sec)資料成員設定為 NULL。

## <a name="ccomcriticalsectioninit"></a><a name="init"></a>CCom臨界部分::Init

調用 Win32 函數[初始化關鍵節](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection),它初始化[m_sec](#m_sec)資料成員中包含的關鍵部分物件。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK成功、E_OUTOFMEMORY或失敗E_FAIL。

## <a name="ccomcriticalsectionlock"></a><a name="lock"></a>CCom臨界部分:鎖

呼叫 Win32 函數[Enter 關鍵節](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection),它等待線程可以取得[m_sec](#m_sec)資料成員中包含的關鍵部分物件的擁有權。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK成功、E_OUTOFMEMORY或失敗E_FAIL。

### <a name="remarks"></a>備註

關鍵節物件必須首先用調用[Init](#init)方法初始化。 當受保護的代碼完成執行後,線程必須調用[Unlock](#unlock)以釋放關鍵部分的擁有權。

## <a name="ccomcriticalsectionm_sec"></a><a name="m_sec"></a>CCom臨界部分:m_sec

包含所有`CComCriticalSection`方法使用的關鍵節物件。

```
CRITICAL_SECTION m_sec;
```

## <a name="ccomcriticalsectionterm"></a><a name="term"></a>CCom臨界部分::學期

呼叫 Win32 函數[Delete關鍵節](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection),它釋放資料成員中包含的關鍵節物件使用的所有資源[m_sec。](#m_sec)

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

調用`Term`後,關鍵部分不能再用於同步。

## <a name="ccomcriticalsectionunlock"></a><a name="unlock"></a>CCom臨界部分:解鎖

調用 Win32 函數[Leave臨界節](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection),它釋放[m_sec](#m_sec)資料成員中包含的關鍵部分物件的擁有權。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK。

### <a name="remarks"></a>備註

要首先獲得擁有權,線程必須調用[Lock](#lock)方法。 每個調用`Lock`都需要相應的調用`Unlock`以 釋放關鍵部分的擁有權。

## <a name="see-also"></a>另請參閱

[CComFake臨界科類](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComCritSeclock 類別](../../atl/reference/ccomcritseclock-class.md)
