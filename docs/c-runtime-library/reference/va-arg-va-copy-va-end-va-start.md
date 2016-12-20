---
title: "va_arg、va_copy、va_end、va_start | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "va_arg"
  - "va_end"
  - "va_copy"
  - "va_start"
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
  - "va_arg"
  - "va_start"
  - "va_list"
  - "va_alist"
  - "va_dcl"
  - "va_copy"
  - "va_end"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "變數引數清單存取"
  - "va_start 巨集"
  - "va_arg 巨集"
  - "va_end 巨集"
  - "引數 [c + +] 引數清單"
  - "va_list 巨集"
  - "va_dcl 巨集"
  - "va_alist 巨集"
  - "va_copy 巨集"
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# va_arg、va_copy、va_end、va_start
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

存取變數引數清單。  
  
## <a name="syntax"></a>語法  
  
```  
  
      type va_arg(  
   va_list arg_ptr,  
   type   
);void va_copy(  
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
);  // (Pre-ANSI C89 standardization version)  
```  
  
#### <a name="parameters"></a>參數  
 `type`  
 要擷取的引數的型別。  
  
 `arg_ptr`  
 引數清單的指標。  
  
 `dest`  
 要從其中初始化的引數清單的指標 `src`  
  
 `src`  
 初始化清單複製到引數的指標 `dest`。  
  
 `prev_param`  
 位於第一個選擇性引數的參數。  
  
## <a name="return-value"></a>傳回值  
 `va_arg` 傳回目前的引數。 `va_copy`, `va_start` 和 `va_end` 不會傳回值。  
  
## <a name="remarks"></a>備註  
  `va_arg`, ，`va_copy`, ，`va_end`, ，和 `va_start` 巨集提供的可攜式方法，以存取函式的引數，當函式接受可變引數數目。 有兩個版本的巨集︰ STDARG 中定義的巨集。H 符合 ISO C99 標準。VARARGS 中定義的巨集。H 已被取代，但會保留回溯相容性的標準 ANSI C89 之前所撰寫的程式碼。  
  
 這些巨集假設函式接受必要的引數，後面接著選擇性的引數數目可變的固定的數。 必要的引數會宣告為函式的一般參數，並可存取透過參數名稱。 選擇性的引數被經由 STDARG 中的巨集。H （或 VARARGS。H ANSI C89 標準之前所撰寫的程式碼)，其設定的指標引數清單中第一個選擇性引數從清單中，擷取引數和引數處理完成時，會重設指標。  
  
 C 標準定義的巨集，在 STDARG。H，用法如下︰  
  
-   `va_start` 設定 `arg_ptr` 傳遞至函數的引數清單中第一個選擇性的引數。 引數 `arg_ptr` 必須 `va_list` 型別。 引數 `prev_param` 是必要引數清單中前面的第一個選擇性引數的參數名稱。 如果 `prev_param` 暫存器儲存類別中，使用巨集的行為未定義宣告。 `va_start` 之前，必須使用 `va_arg` 用於第一次。  
  
-   `va_arg` 擷取某個值的 `type` 由所指定的位置 `arg_ptr`, ，並遞增 `arg_ptr` 指向清單中的下一個引數使用的大小 `type` 來決定下一個引數的開始位置。 `va_arg` 可以是函式使用次數不限，來擷取引數清單中。  
  
-   `va_copy` 建立引數清單的複本處於目前狀態。  `src` 參數必須已經使用初始化 `va_start`; 它可能已更新為 `va_arg` 呼叫，但必須有尚未重設與 `va_end`。 下一個引數所擷取 `va_arg` 從 `dest` 擷取自下一個引數相同 `src`。  
  
-   在擷取所有引數之後， `va_end` 重設的指標 **NULL**。 `va_end` 必須在每個引數清單，以初始化呼叫 `va_start` 或 `va_copy` 函式會傳回之前。  
  
> [!NOTE]
>  VARARGS 巨集。H 已被取代而只保留給回溯相容性以 ANSI C89 標準之前所撰寫的程式碼。 在其他情況下，使用 STDARGS 中的巨集。H.  
  
 當編譯使用 [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md), ，使用這些巨集的程式可能會產生非預期的結果，因為原生和 common language runtime (CLR) 型別系統之間的差異。 此程式，請考慮︰  
  
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
}  
  
int main()  
{  
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int  
    testit(1, NULL);       // 2nd problem: NULL is not a char*  
}  
```  
  
 請注意， `testit` 第二個參數會是 `int` 或 `char*`。 傳入的引數是 0xffffffff ( `unsigned int`, ，而非 `int`) 和 `NULL` (實際上 `int`, ，而非 `char*`)。 當程式編譯為原生程式碼時，它會產生以下輸出︰  
  
```Output  
-1  
  
(null)  
```  
  
 不過，當程式編譯使用 **/clr: pure**, ，類型不符的情況會產生例外狀況。 解決方法是使用明確轉換 （cast）︰  
  
```  
int main()  
{  
   testit( 0, (int)0xFFFFFFFF ); // cast unsigned to int  
   testit( 1, (char*)NULL );     // cast int to char*  
}  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< stdio.h > 和 \< g.h >  
  
 **已被取代的標頭︰** \< varargs.h >  
  
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
  
## <a name="see-also"></a>請參閱  
 [引數存取](../../c-runtime-library/argument-access.md)   
 [vfprintf、 _vfprintf_l、 vfwprintf、 _vfwprintf_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)