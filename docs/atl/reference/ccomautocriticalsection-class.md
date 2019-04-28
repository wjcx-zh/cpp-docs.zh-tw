---
title: CComAutoCriticalSection 類別
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 613440eceb71f0277f4cc5de2af89fe263772797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260185"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 類別

`CComAutoCriticalSection` 提供方法來取得和釋放重要區段物件的擁有權。

## <a name="syntax"></a>語法

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|建構函式。|
|[CComAutoCriticalSection::~CComAutoCriticalSection](#dtor)|解構函式。|

## <a name="remarks"></a>備註

`CComAutoCriticalSection` 類似於類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，除了`CComAutoCriticalSection`自動初始化建構函式中的重要區段物件。

一般而言，您可以使用`CComAutoCriticalSection`經由`typedef`名稱[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)。 此名稱會參考`CComAutoCriticalSection`時[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)正在使用。

`Init`並`Term`方法，從[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)不適用於使用這個類別。

## <a name="inheritance-hierarchy"></a>繼承階層

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>需求

**標頭：** atlcore.h

##  <a name="ccomautocriticalsection"></a>  CComAutoCriticalSection::CComAutoCriticalSection

建構函式。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>備註

呼叫 Win32 函式[InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection)，其初始化的重要區段物件。

##  <a name="dtor"></a>  CComAutoCriticalSection:: ~ CComAutoCriticalSection

解構函式。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>備註

解構函式呼叫[DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection)，這會釋放重要區段物件所使用的所有系統資源。

## <a name="see-also"></a>另請參閱

[CComFakeCriticalSection 類別](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)
