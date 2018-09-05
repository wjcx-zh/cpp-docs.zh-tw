---
title: CComFakeCriticalSection 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection
- ATLCORE/ATL::CComFakeCriticalSection::Init
- ATLCORE/ATL::CComFakeCriticalSection::Lock
- ATLCORE/ATL::CComFakeCriticalSection::Term
- ATLCORE/ATL::CComFakeCriticalSection::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CComFakeCriticalSection class
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48b120b7be3e605b6ed2619cbd71011b0a693bdc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757272"
---
# <a name="ccomfakecriticalsection-class"></a>CComFakeCriticalSection 類別

這個類別會提供相同的方法， [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)但並不會提供重要的區段。

## <a name="syntax"></a>語法

```
class CComFakeCriticalSection
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComFakeCriticalSection::Init](#init)|沒有任何作用，因為沒有任何重要的區段。|
|[CComFakeCriticalSection::Lock](#lock)|沒有任何作用，因為沒有任何重要的區段。|
|[CComFakeCriticalSection::Term](#term)|沒有任何作用，因為沒有任何重要的區段。|
|[CComFakeCriticalSection::Unlock](#unlock)|沒有任何作用，因為沒有任何重要的區段。|

## <a name="remarks"></a>備註

`CComFakeCriticalSection` 鏡像中找到的方法[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)。 不過，`CComFakeCriticalSection`不會提供重要的區段中; 因此，其方法會執行任何動作。

一般而言，您可以使用`CComFakeCriticalSection`經由`typedef`名稱，或是`AutoCriticalSection`或`CriticalSection`。 使用時[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)或是[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這兩種`typedef`名稱參考`CComFakeCriticalSection`。 使用時[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)，它們會參考[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)和`CComCriticalSection`分別。

## <a name="requirements"></a>需求

**標頭：** atlcore.h

##  <a name="init"></a>  CComFakeCriticalSection::Init

沒有任何作用，因為沒有任何重要的區段。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="lock"></a>  CComFakeCriticalSection::Lock

沒有任何作用，因為沒有任何重要的區段。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="term"></a>  CComFakeCriticalSection::Term

沒有任何作用，因為沒有任何重要的區段。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="unlock"></a>  CComFakeCriticalSection::Unlock

沒有任何作用，因為沒有任何重要的區段。

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
