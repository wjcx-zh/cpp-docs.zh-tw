---
title: _get_wpgmptr
ms.date: 11/04/2016
api_name:
- _get_wpgmptr
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 0cd2dc9c2f82d3dc49a17dc438157233c50b3261
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955563"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

取得 **_wpgmptr**全域變數的目前值。

## <a name="syntax"></a>語法

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
要填入 **_wpgmptr**變數目前值的字串指標。

## <a name="return-value"></a>傳回值

如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果*pValue*為**Null**，則會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回**EINVAL**。

## <a name="remarks"></a>備註

只有在您的程式具有寬進入點（例如**wmain （）** 或**wWinMain （））** 時，才呼叫 **_get_wpgmptr** 。 **_Wpgmptr** global 變數包含與進程相關聯之可執行檔的完整路徑，做為寬字元字串。 如需詳細資訊，請參閱 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_get_pgmptr](get-pgmptr.md)<br/>
