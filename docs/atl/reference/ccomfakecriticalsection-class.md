---
title: CComFakeCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
ms.openlocfilehash: 5ada0fbed705af34391709653dbd3638fed32bf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226577"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 類別

這個類別提供的方法與[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)相同，但不提供重要區段。

## <a name="syntax"></a>語法

```
class CComFakeCriticalSection
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CComFakeCriticalSection：： Init](#init)|不會執行任何操作，因為沒有重要區段。|
|[CComFakeCriticalSection：： Lock](#lock)|不會執行任何操作，因為沒有重要區段。|
|[CComFakeCriticalSection：： Term](#term)|不會執行任何操作，因為沒有重要區段。|
|[CComFakeCriticalSection：： Unlock](#unlock)|不會執行任何操作，因為沒有重要區段。|

## <a name="remarks"></a>備註

`CComFakeCriticalSection`鏡像[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)中找到的方法。 不過，不 `CComFakeCriticalSection` 提供重要區段，因此其方法不會執行任何動作。

一般來說，您可以 `CComFakeCriticalSection` 透過或來使用 **`typedef`** `AutoCriticalSection` `CriticalSection` 。 使用[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)時，這兩個名稱都是 **`typedef`** 參考 `CComFakeCriticalSection` 。 使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)時，它們會分別參考[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和 `CComCriticalSection` 。

## <a name="requirements"></a>需求

**標頭：** atlcore。h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CComFakeCriticalSection：： Init

不會執行任何操作，因為沒有重要區段。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFakeCriticalSection：： Lock

不會執行任何操作，因為沒有重要區段。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFakeCriticalSection：： Term

不會執行任何操作，因為沒有重要區段。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFakeCriticalSection：： Unlock

不會執行任何操作，因為沒有重要區段。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
