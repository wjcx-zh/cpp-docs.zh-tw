---
title: _get_pgmptr
ms.date: 4/2/2020
api_name:
- _get_pgmptr
- _o__get_pgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_pgmptr
- _get_pgmptr
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: efcac6a64c01bee38a3753bdec378dae625db35e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345014"
---
# <a name="_get_pgmptr"></a>_get_pgmptr

獲取 **_pgmptr**全域變數的當前值。

## <a name="syntax"></a>語法

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
指向要填充 **_pgmptr**變數的當前值的字串的指標。

## <a name="return-value"></a>傳回值

如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果*pValue*為**NULL,** 則無效參數處理程式將呼叫[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續,此函數將**errno**設定到**EINVAL**並傳回**EINVAL**。

## <a name="remarks"></a>備註

僅當程式的入口點(如**main()** 或**WinMain()))** 時,才呼叫 **_get_pgmptr。** **_pgmptr**全域變數包含與進程關聯的可執行檔的完整路徑。 如需詳細資訊，請參閱 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_get_wpgmptr](get-wpgmptr.md)<br/>
