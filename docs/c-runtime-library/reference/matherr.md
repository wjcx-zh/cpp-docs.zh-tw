---
title: _matherr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _matherr
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
apitype: DLLExport
f1_keywords:
- _matherr
- matherr
dev_langs:
- C++
helpviewer_keywords:
- _matherr function
- matherr function
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 20ed6b9111e7dc3a25462ea9d8b79b8e9e842ed0
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="matherr"></a>_matherr
處理數學錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### <a name="parameters"></a>參數  
 *except*  
 包含錯誤資訊之結構的指標。  
  
## <a name="return-value"></a>傳回值  
 _**matherr** 傳回 0 表示錯誤，或傳回非零值表示作業成功。 如果 \_**matherr** 傳回 0，則會顯示錯誤訊息，並將 `errno` 設定為適當的錯誤值。 如果 \_**matherr** 傳回非零值，則不會顯示任何錯誤訊息，且 `errno` 會保持不變。  
  
 如需傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 _**matherr** 函式會處理數學程式庫的浮點函式所產生的錯誤。 如果偵測到錯誤，這些函式會呼叫 \_**matherr**。  
  
 如需特殊錯誤處理，您可以提供 _**matherr** 的不同定義。 如果您使用 C 執行階段程式庫的動態連結版本 (Msvcr90.dll)，您可以將用戶端可執行檔中的預設 \_**matherr** 常式取代成使用者定義的版本。 不過，您無法取代 Msvcr90.dll 之 DLL 用戶端中的預設 `_matherr` 常式。  
  
 如果數學常式中發生錯誤，就會使用 **_exception** 類型結構的指標 (定義於 Math.h 中) 作為引數來呼叫 _**matherr**。 **_exception** 結構包含下列元素。  
  
 **int 類型**  
 例外狀況類型。  
  
 **char \*name**  
 發生錯誤時的函式名稱。  
  
 **double arg1**、**arg2**  
 要傳遞至函式的第一個和第二個 (如果有) 引數。  
  
 **double retval**  
 要由函式傳回的值。  
  
 **type** 指定數學錯誤的類型。 它是定義於 Math.h 中的下列其中一個值。  
  
 `_DOMAIN`  
 引數網域錯誤。  
  
 `_SING`  
 引數奇點。  
  
 `_OVERFLOW`  
 溢位範圍錯誤。  
  
 `_PLOSS`  
 精確度部分遺失。  
  
 `_TLOSS`  
 精確度完全遺失。  
  
 `_UNDERFLOW`  
 結果太小，無法表示 (目前不支援這種狀況)。  
  
 結構成員 **name** 是以 Null 結束的字串指標，其中包含造成錯誤的函式名稱。 結構成員 **arg1** 和 **arg2** 會指定造成錯誤的值 (如果只指定一個引數，則會儲存在 **arg1** 中)。  
  
 指定錯誤的預設傳回值為 **retval**。 如果您變更傳回值，它必須指定是否確實發生錯誤。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_matherr`|\<math.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="output"></a>輸出  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## <a name="see-also"></a>另請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
