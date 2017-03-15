---
title: "va_arg、va_copy、va_end、va_start | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- va_arg
- va_end
- va_copy
- va_start
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
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 5caea89460070402fc8dc5b38912e290d4c5798d
ms.lasthandoff: 02/24/2017

---
# <a name="vaarg-vacopy-vaend-vastart"></a>va_arg、va_copy、va_end、va_start
存取變數引數清單。  
  
## <a name="syntax"></a>語法  
  
```  
type va_arg(  
   va_list arg_ptr,  
   type   
);
void va_copy(  
   va_list dest,  
   va_list src  
); // (ISO C99 and later)  
void va_end(  
   va_list arg_ptr   
);  
void va_start(  
   va_list arg_ptr,  
   prev_param   
); // (ANSI C89 and later)  
void va_start(  
   arg_ptr   
);  // (deprecated Pre-ANSI C89 standardization version)  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 要擷取的引數類型。  
  
 `arg_ptr`  
 引數清單的指標。  
  
 `dest`  
 要從 `src` 初始化之引數清單的指標。  
  
 `src`  
 要複製至 `dest` 之初始化引數清單的指標。  
  
 `prev_param`  
 第一個選擇性引數之前的參數。  
  
## <a name="return-value"></a>傳回值  
 `va_arg` 會傳回目前引數。 `va_copy`、`va_start` 和 `va_end` 未傳回值。  
  
## <a name="remarks"></a>備註  
 `va_arg`、`va_copy`、`va_end` 和 `va_start` 巨集提供可攜式方法，以在函式接受變動數目的引數時存取函式的引數。 巨集有兩個版本︰定義於 STDARG.H 的巨集符合 ISO C99 標準；定義於 VARARGS.H 的巨集已遭取代但仍保留與 ANSI C89 標準之前所撰寫程式碼的回溯相容性。  
  
 這些巨集假設函式接受固定數目的必要引數，後面接著變動數目的選擇性引數。 必要引數會宣告為函式的一般參數，而且可以透過參數名稱進行存取。 選擇性引數是透過 STDARG.H (或 VARARGS.H，適用於在 ANSI C89 標準之前撰寫的程式碼) 中的巨集進行存取，而這個檔案設定引數清單中第一個選擇性引數的指標、從清單中擷取引數，以及在完成引數處理時重設指標。  
  
 定義於 STDARG.H 之 C 標準巨集的使用如下︰  
  
-   `va_start` 會將 `arg_ptr` 設為傳遞至函式之引數清單中的第一個選擇性引數。 `arg_ptr` 引數必須具有 `va_list` 類型。 引數 `prev_param` 是必要參數的名稱，緊接在引數清單中的第一個選擇性引數前面。 如果使用暫存器儲存類別宣告 `prev_param`，則未定義巨集的行為。 第一次使用 `va_arg` 之前，必須先使用 `va_start`。  
  
-   `va_arg` 會擷取 `arg_ptr` 所指定位置中的 `type` 值，並使用 `type` 大小決定下一個引數的開始位置，來遞增 `arg_ptr` 以指向清單中的下一個引數。 在函式中可以使用任意次數的 `va_arg`，來擷取清單中的引數。  
  
-   `va_copy` 會以目前的狀態複製引數清單。 `src` 參數必須已使用 `va_start` 初始化；它可能已使用 `va_arg` 呼叫更新，但尚未使用 `va_end` 重設。 `va_arg` 從 `dest` 擷取的下一個引數，與擷取自 `src` 的下一個引數相同。  
  
-   擷取所有引數之後，`va_end` 會重設 **NULL** 的指標。 傳回函式之前，在使用 `va_start` 或 `va_copy` 初始化的每個引數清單上，都必須呼叫 `va_end`。  
  
> [!NOTE]
>  VARARGS.H 中的巨集已遭取代，並且僅保留與 ANSI C89 標準之前所撰寫程式碼的回溯相容性。 在所有其他情況下，會使用 STDARGS.H 中的巨集。  
  
 因為原生與 Common Language Runtime (CLR) 類型系統之間的差異，所以使用 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，使用這些巨集的程式可能會產生未預期結果。 請考慮使用此程式：  
  
```  
#include <stdio.h>  
#include <stdarg.h>  
  
void testit (int i, ...)  
{  
    va_list argptr;  
    va_start(argptr, i);  
  
    if (i == 0)  
    {  
        int n = va_arg(argptr, int);  
        printf("%d\n", n);  
    }  
    else  
    {  
        char *s = va_arg(argptr, char*);  
        printf("%s\n", s);  
    }  

    va_end(argptr);  
}  
  
int main()  
{  
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int  
    testit(1, NULL);       // 2nd problem: NULL is not a char*  
}  
```  
  
 請注意，`testit` 的第二個參數必須是 `int` 或 `char*`。 正在傳遞的引數是 0xffffffff (`unsigned int`，非 `int`) 和 `NULL` (實際是 `int`，非 `char*`)。 針對機器碼編譯程式時，會產生此輸出︰  
  
```Output  
-1  
  
(null)  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<stdio.h> 和 \<stdarg.h>  
  
 **已取代的標頭︰**\<varargs.h>  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_va.c  
/* Compile with: cl /W3 /Tc crt_va.c  
 * The program below illustrates passing a variable  
 * number of arguments using the following macros:  
 *      va_start            va_arg              va_copy  
 *      va_end              va_list  
 */  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <math.h>  
  
double deviation(int first, ...);  
  
int main( void )  
{  
    /* Call with 3 integers (-1 is used as terminator). */  
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));  
  
    /* Call with 4 integers. */  
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));  
  
    /* Call with just -1 terminator. */  
    printf("Deviation is: %f\n", deviation(-1));  
}  
  
/* Returns the standard deviation of a variable list of integers. */  
double deviation(int first, ...)  
{  
    int count = 0, i = first;  
    double mean = 0.0, sum = 0.0;  
    va_list marker;  
    va_list copy;  
  
    va_start(marker, first);     /* Initialize variable arguments. */  
    va_copy(copy, marker);       /* Copy list for the second pass */  
    while (i != -1)  
    {  
        sum += i;  
        count++;  
        i = va_arg(marker, int);  
    }  
    va_end(marker);              /* Reset variable argument list. */  
    mean = sum ? (sum / count) : 0.0;  
  
    i = first;                  /* reset to calculate deviation */  
    sum = 0.0;  
    while (i != -1)  
    {  
        sum += (i - mean)*(i - mean);  
        i = va_arg(copy, int);  
    }  
    va_end(copy);               /* Reset copy of argument list. */  
    return count ? sqrt(sum / count) : 0.0;  
}  
  
```  
  
## <a name="output"></a>輸出  
  
```Output  
Deviation is: 0.816497  
Deviation is: 2.236068  
Deviation is: 0.000000  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::ParamArrayAttribute 類別](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [引數存取](../../c-runtime-library/argument-access.md)   
 [vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)
