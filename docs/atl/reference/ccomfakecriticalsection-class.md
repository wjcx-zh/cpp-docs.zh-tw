---
title: CComFake臨界科類
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
ms.openlocfilehash: 4a5b9ba3551397a9c3d59a343e9c6b55b1c1207e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327845"
---
# <a name="ccomfakecriticalsection-class"></a>CComFake臨界科類

此類提供的方法與[CCom臨界節](../../atl/reference/ccomcriticalsection-class.md)相同,但不提供關鍵部分。

## <a name="syntax"></a>語法

```
class CComFakeCriticalSection
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CcomFake關鍵部分::Init](#init)|由於沒有關鍵部分,因此不執行任何操作。|
|[CComFake 關鍵部份::鎖定](#lock)|由於沒有關鍵部分,因此不執行任何操作。|
|[CComFake關鍵部分::學期](#term)|由於沒有關鍵部分,因此不執行任何操作。|
|[CComFake關鍵部分::解鎖](#unlock)|由於沒有關鍵部分,因此不執行任何操作。|

## <a name="remarks"></a>備註

`CComFakeCriticalSection`鏡像[CCom臨界節](../../atl/reference/ccomcriticalsection-class.md)中找到的方法。 但是,`CComFakeCriticalSection`不提供關鍵部分;但是,不提供關鍵部分。因此,它的方法什麼都不做。

通常`CComFakeCriticalSection`,您`typedef`可以通過`AutoCriticalSection`名稱`CriticalSection`或 。 當使用[CCom 單線程模型](../../atl/reference/ccomsinglethreadmodel-class.md)或[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)時,這`typedef`兩個名稱`CComFakeCriticalSection`都引用。 使用[CComMultiThread 模型](../../atl/reference/ccommultithreadmodel-class.md)時,它們分別參考[CComAuto 臨界部分](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`。

## <a name="requirements"></a>需求

**標題:** atlcore.h

## <a name="ccomfakecriticalsectioninit"></a><a name="init"></a>CcomFake關鍵部分::Init

由於沒有關鍵部分,因此不執行任何操作。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="ccomfakecriticalsectionlock"></a><a name="lock"></a>CComFake 關鍵部份::鎖定

由於沒有關鍵部分,因此不執行任何操作。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="ccomfakecriticalsectionterm"></a><a name="term"></a>CComFake關鍵部分::學期

由於沒有關鍵部分,因此不執行任何操作。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="ccomfakecriticalsectionunlock"></a><a name="unlock"></a>CComFake關鍵部分::解鎖

由於沒有關鍵部分,因此不執行任何操作。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>傳回值

返回S_OK。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
