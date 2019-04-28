---
title: _get_doserrno
ms.date: 11/04/2016
apiname:
- _get_doserrno
apilocation:
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
apitype: DLLExport
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 700f710e6d94f48b03697325bb720dbc539fe04e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287742"
---
# <a name="getdoserrno"></a>_get_doserrno

取得錯誤所傳回的值的作業系統之前就會轉譯成對**errno**值。

## <a name="syntax"></a>語法

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>參數

*pValue*<br/>
要填入的目前值的整數指標 **_doserrno**全域巨集。

## <a name="return-value"></a>傳回值

如果 **_get_doserrno**成功，則會傳回零; 如果失敗，它會傳回錯誤碼。 如果*pValue*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

## <a name="remarks"></a>備註

**_Doserrno**全域巨集設為零 CRT 初始化期間，處理程序之前開始執行。 此巨集是設定為由會傳回作業系統錯誤的任何系統層級函式呼叫所傳回的作業系統錯誤值，且在執行期間永不重設為 0。 當您撰寫程式碼來檢查錯誤值時傳回的函式，一律清除 **_doserrno**利用[_set_doserrno](set-doserrno.md)函式呼叫之前。 因為另一個函式呼叫可能會覆寫 **_doserrno**，藉由檢查值 **_get_doserrno**函式呼叫之後立即。

我們建議[_get_errno](get-errno.md)而不是 **_get_doserrno**針對可攜式錯誤碼。

可能的值 **_doserrno**中所定義\<errno.h >。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|

**_get_doserrno**是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[_set_doserrno](set-doserrno.md)<br/>
[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
