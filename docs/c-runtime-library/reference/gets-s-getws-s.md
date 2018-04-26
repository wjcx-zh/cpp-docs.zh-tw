---
title: gets_s、_getws_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _getws_s
- gets_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getws_s
- gets_s
dev_langs:
- C++
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efd4e458fa71fd6dcd93d47350c998a4a410cc65
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="getss-getwss"></a>gets_s、_getws_s

取得從行**stdin**資料流。 這些版本的 [fopen、_wfopen](../../c-runtime-library/gets-getws.md) 具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>參數

*buffer*<br/>
輸入字串的儲存體位置。

*sizeInCharacters*<br/>
緩衝區的大小。

## <a name="return-value"></a>傳回值

傳回*緩衝區*如果成功的話。 A **NULL**指標表示錯誤或檔案結尾的條件。 使用 [ferror](ferror.md) 或 [feof](feof.md) 判斷發生的是哪一個事件。

## <a name="remarks"></a>備註

**Gets_s**函式從標準輸入資料流讀取一行**stdin**並將其儲存在*緩衝區*。 此行包括到第一個新行字元 ('\n') (含) 的所有字元。 **gets_s**再以 null 字元 ('\0') 取代新行字元，再傳回該行。 相反地， **fgets_s**函式會保留新行字元。

如果讀取的第一個字元是檔案結尾的字元，null 字元會儲存在開頭*緩衝區*和**NULL**傳回。

**_getws_s**是寬字元版本的**gets_s**; 它的引數和傳回值是寬字元字串。

如果*緩衝區*是**NULL**或*sizeInCharacters*小於或等於零，或如果緩衝區太小，無法包含輸入的行和 null 結束字元時，會叫用這些函式中所述的無效參數處理常式[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函數會傳回**NULL**並將 errno 設**為 ERANGE**。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 應用程式中不支援主控台。 在主控台中，與相關聯的標準資料流控制代碼**stdin**， **stdout**，和**stderr**，必須重新導向之後 C 執行階段函式可以在 UWP 應用程式中使用它們,. 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[gets、_getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets、fgetws](fgets-fgetws.md)<br/>
[fputs、fputws](fputs-fputws.md)<br/>
[puts、_putws](puts-putws.md)<br/>
