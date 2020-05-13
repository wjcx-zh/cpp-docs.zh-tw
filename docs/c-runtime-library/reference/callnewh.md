---
title: _callnewh
ms.date: 4/2/2020
api_name:
- _callnewh
- _o__callnewh
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 3990d4b15c25cfd6c753c2b1d44c112971ff59af
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918792"
---
# <a name="_callnewh"></a>_callnewh

呼叫目前安裝的「新的處理常式」**。

## <a name="syntax"></a>語法

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>參數

*size*<br/>
[new 運算子](../../cpp/new-operator-cpp.md)嘗試配置的記憶體數量。

## <a name="return-value"></a>傳回值

|值|描述|
|-----------|-----------------|
|0|失敗︰未安裝新的處理常式，或沒有新的處理常式作用。|
|1|成功︰新的處理常式已安裝並作用。 可以重試記憶體配置。|

## <a name="exceptions"></a>例外狀況

如果找不到「新的處理常式」**，則此函式會擲回 [bad_alloc](../../standard-library/bad-alloc-class.md)。

## <a name="remarks"></a>備註

如果 [new 運算子](../../cpp/new-operator-cpp.md)無法成功地配置記憶體，則會呼叫「新的處理常式」**。 新的處理常式可能接著會起始一些適當動作，例如釋放記憶體，以讓後續配置成功。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>另請參閱

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
