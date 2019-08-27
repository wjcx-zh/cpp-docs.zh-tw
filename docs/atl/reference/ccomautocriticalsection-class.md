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
ms.openlocfilehash: 116c550f45bf622e7620b3a6f552339b4bcc24a7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497935"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection 類別

`CComAutoCriticalSection`提供取得和釋放重要區段物件之擁有權的方法。

## <a name="syntax"></a>語法

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|建構函式。|
|[CComAutoCriticalSection:: ~ CComAutoCriticalSection](#dtor)|解構函式。|

## <a name="remarks"></a>備註

`CComAutoCriticalSection`類似于類別[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md), 不同之`CComAutoCriticalSection`處在于會自動初始化此函式中的重要區段物件。

一般來說, 您會`CComAutoCriticalSection` `typedef`透過名稱[AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection)來使用。 使用[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)時`CComAutoCriticalSection` , 會參考此名稱。

使用`Init`此`Term`類別時, 無法使用來自[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)的和方法。

## <a name="inheritance-hierarchy"></a>繼承階層

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>需求

**標頭:** atlcore。h

##  <a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection

建構函式。

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>備註

呼叫 Win32 函數[InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection), 這會初始化重要區段物件。

##  <a name="dtor"></a>CComAutoCriticalSection:: ~ CComAutoCriticalSection

解構函式。

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>備註

此析構函式會呼叫[DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection), 這會釋放重要區段物件所使用的所有系統資源。

## <a name="see-also"></a>另請參閱

[CComFakeCriticalSection 類別](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)
