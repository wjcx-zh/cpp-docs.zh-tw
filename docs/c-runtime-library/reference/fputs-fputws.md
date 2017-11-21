---
title: "fputs、fputws | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fputs
- fputws
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
- fputs
- fputws
- _fputts
dev_langs: C++
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5d3d9a9225a3b6bc0dafd8804f62c61a94acb43c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="fputs-fputws"></a>fputs、fputws
將字串寫入資料流。  
  
## <a name="syntax"></a>語法  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>參數  
 `str`  
 輸出字串。  
  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則所有這些函式都會傳回非負值。 發生錯誤時，`fputs` 和 `fputws` 會傳回 `EOF`。 如果 `str` 或 `stream` 是 Null 指標，這些函式會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，然後 `fputs` 會傳回 `EOF`，而且 `fputws` 會傳回 `WEOF`。  
  
 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 所有這些函式都會將 `str` 複製至輸出 `stream` 的目前位置。 `fputws` 會根據以文字模式還是二進位模式開啟 `stream`，分別將寬字元引數 `str` 以多位元組字元字串或寬字元字串形式複製至 `stream`。 任一函式都不會複製終止 Null 字元。  
  
 如果資料流是以 ANSI 模式開啟，則這兩個函式的行為相同。 `fputs` 目前不支援輸出至 UNICODE 資料流。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`fputs`|\<stdio.h>|  
|`fputws`|\<stdio.h> 或 \<wchar.h>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。 與主控台 (`stdin`、`stdout` 和 `stderr`) 關聯的標準資料流控制代碼必須重新導向，之後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
```Output  
Hello world from fputs.  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [gets、_getws](../../c-runtime-library/gets-getws.md)   
 [puts、_putws](../../c-runtime-library/reference/puts-putws.md)