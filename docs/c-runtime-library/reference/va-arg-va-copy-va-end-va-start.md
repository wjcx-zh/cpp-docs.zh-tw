---
title: va_arg、va_copy、va_end、va_start
ms.date: 11/04/2016
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
ms.openlocfilehash: cc0a903f6bc4895f7d2ea6e80990dea94f28c6c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353562"
---
# <a name="vaarg-vacopy-vaend-vastart"></a>va_arg、va_copy、va_end、va_start

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
從初始化的引數清單的指標*src*

*src*<br/>
要複製到的引數初始化清單指標*dest*。

*prev_param*<br/>
第一個選擇性引數之前的參數。

## <a name="return-value"></a>傳回值

**va_arg**傳回目前引數。 **va_copy**， **va_start**並**va_end**不會傳回值。

## <a name="remarks"></a>備註

**Va_arg**， **va_copy**， **va_end**，以及**va_start**巨集提供可攜式方法來存取函式引數時函數會採用可變數目的引數。 有兩個版本的巨集：STDARG 中定義的巨集。H 符合 ISO C99 標準;在 VARARGS 中定義的巨集。H 已被取代，但仍保留與 ANSI C89 標準之前所撰寫的程式碼的回溯相容性。

這些巨集假設函式接受固定數目的必要引數，後面接著變動數目的選擇性引數。 必要引數會宣告為函式的一般參數，而且可以透過參數名稱進行存取。 選擇性引數是透過 STDARG.H (或 VARARGS.H，適用於在 ANSI C89 標準之前撰寫的程式碼) 中的巨集進行存取，而這個檔案設定引數清單中第一個選擇性引數的指標、從清單中擷取引數，以及在完成引數處理時重設指標。

定義於 STDARG.H 之 C 標準巨集的使用如下︰

- **va_start**設定*arg_ptr*来傳遞至函數的引數清單中的第一個選擇性引數。 引數*arg_ptr*必須**va_list**型別。 引數*prev_param*引數清單中前面的第一個選擇性引數的必要參數的名稱。 如果*prev_param*暫存器儲存類別中，使用巨集的行為未定義宣告。 **va_start**之前，必須使用**va_arg**用於第一次。

- **va_arg**擷取的值*型別*所指定的位置*arg_ptr*，並遞增*arg_ptr*指向清單中下一個引數使用的大小*型別*以判斷下一個引數的開始位置。 **va_arg**可以是函式中的任意數目的時間用來從清單中擷取引數。

- **va_copy**會建立一份引數清單，在其目前的狀態。 *Src*參數必須已經使用初始化**va_start**; 它可能已透過更新**va_arg**呼叫，但必須不具有已重設與**va_end**. 擷取下一個引數**va_arg**從*dest*等同於下一步擷取自的引數*src*。

- 在擷取所有引數之後， **va_end**重設指標**NULL**。 **va_end**上會使用初始化每個引數清單必須呼叫**va_start**或是**va_copy**函式會傳回之前。

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

請注意， **testit**需要其第二個參數必須是**int**或是**char**<strong>\*</strong>。 正在傳遞的引數是 0xffffffff (**不帶正負號** **int**，而非**int**) 以及**NULL** (實際上**int**，而非**char**<strong>\*</strong>)。 針對機器碼編譯程式時，會產生此輸出︰

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
