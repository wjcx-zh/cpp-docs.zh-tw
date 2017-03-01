---
title: "vfscanf_s、vfwscanf_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vfscanf_s
- vfwscanf_s
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
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
dev_langs:
- C++
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
caps.latest.revision: 6
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 17f7f284bfa8cacc895949f5392b009bc86ee427
ms.lasthandoff: 02/24/2017

---
# <a name="vfscanfs-vfwscanfs"></a>vfscanf_s、vfwscanf_s
從資料流讀取格式化資料。 這些版本的 vfscanf、vfwscanf 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
int vfscanf_s(   
   FILE *stream,  
   const char *format,  
   va_list arglist  
);  
int vfwscanf_s(   
   FILE *stream,  
   const wchar_t *format,  
   va_list arglist  
);  
  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
 `format`  
 格式控制字串。  
  
 `arglist`  
 變數引數清單。  
  
## <a name="return-value"></a>傳回值  
 所有這些函式都會傳回已成功轉換並指派的欄位數，傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 如果發生錯誤，或進行第一次轉換之前就到達檔案資料流結尾，則 `vfscanf_s` 和 `vfwscanf_s` 的傳回值是 `EOF`。  
  
 這些函式會驗證它們的參數。 如果 `stream` 是無效檔案指標，或 `format` 為 Null 指標，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會傳回 `EOF`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `vfscanf_s` 函式會將 `stream` 之目前位置的資料讀入 `arglist` 引數清單 (如果有的話) 所指定的位置。 清單中的每個引數都必須是變數的指標，而變數的類型對應至 `format` 中的類型指定名稱。 `format` 會控制輸入欄位的解譯，而且形式和功能與 `scanf_s` 的 `format` 引數相同；如需 `format` 的描述，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。 `vfwscanf_s` 是 `vfscanf_s` 的寬字元版本；`vfwscanf_s` 的格式引數是寬字元字串。 如果資料流是以 ANSI 模式開啟，則這些函式的行為相同。 `vfscanf_s` 目前不支援來自 UNICODE 資料流的輸入。  
  
 較安全的函式 (具有 `_s` 字尾) 和其他版本主要的不同在於，較安全的函式要求每個 `c`、`C`、`s`、`S`和 `[` 類型欄位的大小 (以字元為單位) 都要緊接在變數後以引數的方式傳遞。 如需詳細資訊，請參閱 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小參數為型別 `unsigned`，而非 `size_t`。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftscanf_s`|`vfscanf_s`|`vfscanf_s`|`vfwscanf_s`|  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`vfscanf_s`|\<stdio.h>|  
|`vfwscanf_s`|\<stdio.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_vfscanf_s.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf_s to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int call_vfscanf_s(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf_s(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)  
    {  
        printf("The file vfscanf_s.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
    }  
}  
  
```  
  
```Output  
a-string  
65000  
3.141590  
x  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx)。 請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [fscanf、_fscanf_l、fwscanf、_fwscanf_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [vfscanf、vfwscanf](../../c-runtime-library/reference/vfscanf-vfwscanf.md)
