---
title: "_matherr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_matherr"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_matherr"
  - "matherr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_matherr 函式"
  - "matherr 函式"
ms.assetid: b600d66e-165a-4608-a856-8fb418d46760
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _matherr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理算術錯誤。  
  
## 語法  
  
```  
  
      int _matherr(  
   struct _exception *except   
);  
```  
  
#### 參數  
 *except*  
 包含錯誤資訊之結構的指標。  
  
## 傳回值  
 \_**matherr** 傳回 0 以指示錯誤或非零值為表示成功。  如果 \_**matherr** 傳回 0，錯誤訊息的顯示，而且 `errno` 設定為適當的錯誤值。  如果 \_**matherr** 傳回非零值，錯誤訊息不會顯示，而 `errno` 則會保持不變。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 數學程式庫的浮點函式產生 \_**matherr** 函式來處理錯誤。  這些函式呼叫 \_**matherr** ，在偵測到錯誤。  
  
 如需特殊的錯誤處理，您可以提供 \_**matherr**的不同的定義。  如果您使用 C 執行階段程式庫 \(Msvcr90.dll\) 的動態連接的版本，您可以用使用者定義的版本取代用戶端可執行檔的預設 \_**matherr** 常式。  不過，您不能取代在 DLL Msvcr90.dll 的用戶端的預設 `_matherr` 常式。  
  
 當錯誤發生在數學常式時發生錯誤， \_**matherr** 和 **\_exception** 呼叫對型別結構指標 \(定義於 Math.h\) 做為引數。  該**例外狀況**結構包含下列元素：  
  
 型別：**int型別**  
 例外狀況類型。  
  
 **char \*name**  
 發生錯誤的函式名稱。  
  
 **double arg1**， **arg2**  
 對函式的第一個和第二個 \(如果有的話\) 引數。  
  
 **double retval**  
 函式所傳回的值。  
  
 **type** 指定算術錯誤類型。  它是下列其中一個值，定義在 Math.h。  
  
 `_DOMAIN`  
 引數網域錯誤。  
  
 `_SING`  
 引數稀有。  
  
 `_OVERFLOW`  
 溢位範圍錯誤。  
  
 `_PLOSS`  
 重要性部分遺失。  
  
 `_TLOSS`  
 完整顯著性位元遺失。  
  
 `_UNDERFLOW`  
 結果太小而無法表示。\(這個條件目前不支援。\)  
  
 結構成員 **name** 是指向包含造成錯誤的函式名稱的 NULL 結尾字串。  結構成員 **arg1** 和 **arg2** 指定造成錯誤的值。\(如果只將一個引數，它在 **arg1**儲存\)。  
  
 指定之錯誤的預設傳回值為 **retval**。  如果您變更傳回值之前，必須先指定錯誤是否確實發生錯誤。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_matherr`|\<math.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
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
  
## Output  
  
```  
Special: using absolute value: log: _DOMAIN error  
log( -2.0 ) = 6.931472e-001  
Special: using absolute value: log10: _DOMAIN error  
log10( -5.0 ) = 6.989700e-001  
Normal: log( 0.0 ) = -1.#INF00e+000  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [長雙精度](../../misc/long-double.md)