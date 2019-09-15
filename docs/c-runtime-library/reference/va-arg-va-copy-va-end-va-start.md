---
title: va_arg、va_copy、va_end、va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
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
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
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
ms.openlocfilehash: 47bd9e3913c6664a52c970dd8a190636683d214e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957357"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg、va_copy、va_end、va_start

存取變數引數清單。

## <a name="syntax"></a>語法

```C
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

### <a name="parameters"></a>參數

*type*<br/>
要擷取的引數類型。

*arg_ptr*<br/>
引數清單的指標。

*dest*<br/>
要從*src*初始化之引數清單的指標

*src*<br/>
要複製到*目的地*之引數的已初始化清單的指標。

*prev_param*<br/>
第一個選擇性引數之前的參數。

## <a name="return-value"></a>傳回值

**va_arg**會傳回目前的引數。 **va_copy**、 **va_start**和**va_end**不會傳回值。

## <a name="remarks"></a>備註

**Va_arg**、 **va_copy**、 **va_end**和**va_start**宏可在函式接受可變數目的引數時，提供可移植的方式來存取函式的引數。 有兩個版本的宏：STDARG.H> 中定義的宏。H 符合 ISO C99 標準;以 VARARGS 定義的宏。H 已被取代，但為了與 ANSI C89 標準之前所撰寫的程式碼具有回溯相容性而保留。

這些巨集假設函式接受固定數目的必要引數，後面接著變動數目的選擇性引數。 必要引數會宣告為函式的一般參數，而且可以透過參數名稱進行存取。 選擇性引數是透過 STDARG.H (或 VARARGS.H，適用於在 ANSI C89 標準之前撰寫的程式碼) 中的巨集進行存取，而這個檔案設定引數清單中第一個選擇性引數的指標、從清單中擷取引數，以及在完成引數處理時重設指標。

定義於 STDARG.H 之 C 標準巨集的使用如下︰

- **va_start**會將*arg_ptr*設定為傳遞至函數之引數清單中的第一個選擇性引數。 引數*arg_ptr*必須具有**va_list**類型。 引數*prev_param*是緊接在引數清單中第一個選擇性引數之前的必要參數名稱。 如果*prev_param*是以 register 儲存類別宣告，則宏的行為會是未定義的。 第一次使用**va_arg**之前，必須先使用**va_start** 。

- **va_arg**會從*arg_ptr*所提供的位置抓取*類型*的值，並使用*類型*的大小來決定下一個引數的開始，以遞增*arg_ptr*以指向清單中的下一個引數。 **va_arg**可以在函式中使用任意次數的次數，以從清單中取出引數。

- **va_copy**會以目前的狀態複製引數清單。 *Src*參數必須已經使用**va_start**初始化;它可能已透過**va_arg**呼叫更新，但不能使用**va_end**重設。 **Va_arg**從*dest*取出的下一個引數，與從*src*抓取的下一個引數相同。

- 取得所有引數之後， **va_end**會將指標重設為**Null**。 在函式傳回之前，必須在使用**va_start**或**va_copy**初始化的每個引數清單上呼叫**va_end** 。

> [!NOTE]
> VARARGS.H 中的巨集已遭取代，並且僅保留與 ANSI C89 標準之前所撰寫程式碼的回溯相容性。 在所有其他情況下，會使用 STDARGS.H 中的巨集。

因為原生與 Common Language Runtime (CLR) 類型系統之間的差異，所以使用 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md) 進行編譯時，使用這些巨集的程式可能會產生未預期結果。 請考慮使用此程式：

```C
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

請注意， **testit**預期其第二個參數必須是**int**或**char** <strong>\*</strong>。 所傳遞的引數是0xffffffff （不**帶正負**號的**整數**，而不是**int**）和**Null** （實際上是**int**，而不是**char** <strong>\*</strong>）。 針對機器碼編譯程式時，會產生此輸出︰

```Output
-1

(null)
```

## <a name="requirements"></a>需求

**標頭：** \<stdio.h> 和 \<stdarg.h>

**已取代的標頭︰** \<varargs.h>

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

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

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>另請參閱

[引數存取](../../c-runtime-library/argument-access.md)<br/>
[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
