---
title: CComSimpleThreadAllocator 類別
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: 1644014048b27b7ab6076783c5025140527a7ff5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637537"
---
# <a name="ccomsimplethreadallocator-class"></a>CComSimpleThreadAllocator 類別

此類別會管理類別選取執行緒`CComAutoThreadModule`。

## <a name="syntax"></a>語法

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|選取一個執行緒。|

## <a name="remarks"></a>備註

`CComSimpleThreadAllocator` 管理針對選取的執行緒[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。 `CComSimpleThreadAllocator::GetThread` 只要每個執行緒，並傳回序列中的下一個。

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread

選取一個執行緒，藉由指定序列中的下一個執行緒。

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>參數

*pApt*<br/>
不使用 ATL 的預設實作。

*nThreads*<br/>
EXE 模組中的執行緒數目上限。

### <a name="return-value"></a>傳回值

整數，介於 0 和 (*nThreads* -1)。 識別其中一個 EXE 模組中的執行緒。

### <a name="remarks"></a>備註

您可以覆寫`GetThread`提供的選取項目不同的方法，或將使用*pApt*參數。

`GetThread` 會呼叫[CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance)。

## <a name="see-also"></a>另請參閱

[CComApartment 類別](../../atl/reference/ccomapartment-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
