---
title: _matherr
ms.date: 04/05/2018
api_name:
- _matherr
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _matherr
- matherr
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
ms.openlocfilehash: 340e3b8562e1f0f564810bc63cf6bd2e87ffdf63
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952763"
---
# <a name="_matherr"></a>_matherr

處理數學錯誤。

## <a name="syntax"></a>語法

```C
int _matherr( struct _exception * except );
```

### <a name="parameters"></a>參數

*except*<br/>
包含錯誤資訊之結構的指標。

## <a name="return-value"></a>傳回值

**_matherr**會傳回0來表示錯誤，或傳回非零值表示成功。 如果 **_matherr**傳回0，則會顯示錯誤訊息，而且**errno**會設定為適當的錯誤值。 如果 **_matherr**傳回非零值，則不會顯示任何錯誤訊息，而且**errno**會保持不變。

如需傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Matherr**函式會處理 math 程式庫的浮點函式所產生的錯誤。 當偵測到錯誤時，這些函式會呼叫 **_matherr** 。

針對特殊的錯誤處理，您可以提供不同的 **_matherr**定義。 如果您使用的是 C 執行時間程式庫（CRT）的動態連結版本，您可以使用使用者定義的版本來取代用戶端可執行檔中的預設 **_matherr**常式。 不過，您無法在 CRT DLL 的 DLL 用戶端中取代預設的 **_matherr**常式。

當 math 常式發生錯誤時，會呼叫 **_matherr** ，並以指標指向 **_exception**類型結構（定義于\<math >）做為引數。 **_exception** 結構包含下列元素。

```C
struct _exception
{
    int    type;   // exception type - see below
    char*  name;   // name of function where error occurred
    double arg1;   // first argument to function
    double arg2;   // second argument (if any) to function
    double retval; // value to be returned by function
};
```

**類型**成員會指定 math 錯誤的類型。 它是下列其中一個值（定義于\<math. h >：

|巨集|意義|
|-|-|
| **_DOMAIN** | 引數網域錯誤 |
| **_SING** | 引數 singularity |
| **_OVERFLOW** | 溢位範圍錯誤 |
| **_PLOSS** | 重要性的部分遺失 |
| **_TLOSS** | 總失去的重要性 |
| **_UNDERFLOW** | 結果太小，無法表示 (目前不支援這種狀況)。 |

結構成員 **name** 是以 Null 結束的字串指標，其中包含造成錯誤的函式名稱。 結構成員 **arg1** 和 **arg2** 會指定造成錯誤的值 如果只指定一個引數，它就會儲存在**arg1**中。

指定錯誤的預設傳回值為 **retval**。 如果您變更傳回值，它必須指定是否確實發生錯誤。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_matherr**|\<math.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_matherr.c
/* illustrates writing an error routine for math
* functions. The error function must be:
*      _matherr
*/

#include <math.h>
#include <string.h>
#include <stdio.h>

int main()
{
    /* Do several math operations that cause errors. The _matherr
     * routine handles _DOMAIN errors, but lets the system handle
     * other errors normally.
     */
    printf( "log( -2.0 ) = %e\n", log( -2.0 ) );
    printf( "log10( -5.0 ) = %e\n", log10( -5.0 ) );
    printf( "log( 0.0 ) = %e\n", log( 0.0 ) );
}

/* Handle several math errors caused by passing a negative argument
* to log or log10 (_DOMAIN errors). When this happens, _matherr
* returns the natural or base-10 logarithm of the absolute value
* of the argument and suppresses the usual error message.
*/
int _matherr( struct _exception *except )
{
    /* Handle _DOMAIN errors for log or log10. */
    if( except->type == _DOMAIN )
    {
        if( strcmp( except->name, "log" ) == 0 )
        {
            except->retval = log( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
        else if( strcmp( except->name, "log10" ) == 0 )
        {
            except->retval = log10( -(except->arg1) );
            printf( "Special: using absolute value: %s: _DOMAIN "
                     "error\n", except->name );
            return 1;
        }
    }
    printf( "Normal: " );
    return 0;    /* Else use the default actions */
}
```

```Output
Special: using absolute value: log: _DOMAIN error
log( -2.0 ) = 6.931472e-01
Special: using absolute value: log10: _DOMAIN error
log10( -5.0 ) = 6.989700e-01
Normal: log( 0.0 ) = -inf
```

## <a name="see-also"></a>另請參閱

[浮點支援](../../c-runtime-library/floating-point-support.md)<br/>
