---
title: CCom 簡單線程定位器類別
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
ms.openlocfilehash: 4a3cce492db4db9f46aeb4efe738ee6a594ddcfc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327337"
---
# <a name="ccomsimplethreadallocator-class"></a>CCom 簡單線程定位器類別

此類管理類`CComAutoThreadModule`的線程選擇。

## <a name="syntax"></a>語法

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCom 簡單線程定位器:抓取緒](#getthread)|選擇線程。|

## <a name="remarks"></a>備註

`CComSimpleThreadAllocator`管理[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)的線程選擇。 `CComSimpleThreadAllocator::GetThread`只需迴圈遍過每個線程,然後返回序列中的下一個線程。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomsimplethreadallocatorgetthread"></a><a name="getthread"></a>CCom 簡單線程定位器:抓取緒

通過指定序列中的下一個線程來選擇線程。

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>參數

*pApt*<br/>
未用於 ATL 的預設實現。

*nThreads*<br/>
EXE 模組中的最大線程數。

### <a name="return-value"></a>傳回值

零和 *(nThreads* - 1) 之間的整數。 標識 EXE 模組中的一個線程。

### <a name="remarks"></a>備註

您可以重寫`GetThread`以提供不同的選擇方法或使用*pApt*參數。

`GetThread`由[CComAutoThreadModule 呼叫::建立實體 。](../../atl/reference/ccomautothreadmodule-class.md#createinstance)

## <a name="see-also"></a>另請參閱

[CCom公寓類別](../../atl/reference/ccomapartment-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
