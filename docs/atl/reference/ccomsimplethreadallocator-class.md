---
title: CComSimpleThreadAllocator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1538d5148eeb1eb95c51150a43ef5dd7b107cae3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033546"
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
