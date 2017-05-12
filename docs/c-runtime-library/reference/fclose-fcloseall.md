---
title: "fclose、_fcloseall | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 46b9086e4c75a699acec47e3b6b68ba7bcc231cf
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="fclose-fcloseall"></a>fclose、_fcloseall
關閉資料流 (`fclose`) 或關閉所有開啟的資料流 (`_fcloseall`)。  
  
## <a name="syntax"></a>語法  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功關閉資料流，`fclose` 會傳回 0。 `_fcloseall` 會傳回關閉的資料流總數。 兩個函式都傳回 `EOF` 表示錯誤。  
  
## <a name="remarks"></a>備註  
 `fclose` 函式會關閉 `stream`。 如果 `stream` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`fclose` 會將 `errno` 設為 `EINVAL` 且傳回 `EOF`。 建議在呼叫此函式前，一律先勾選 `stream` 指標。  
  
 如需這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `_fcloseall` 函式會關閉所有開啟的資料流，除了`stdin`、`stdout`、`stderr` (MS-DOS 要加上 `_stdaux` 和 `_stdprn`)。 它也會關閉並刪除 `tmpfile` 建立的所有暫存檔案。 在這兩個函式中，所有與資料流相關聯的緩衝區都會先排清再關閉。 關閉資料流時，會釋放系統配置的緩衝區。 不會自動釋放使用者以 `setbuf` 和 `setvbuf` 指派的緩衝區。  
  
 **注意︰**使用這些函式關閉資料流時，基礎檔案描述項和作業系統檔案控制代碼 (或通訊端) 以及資料流都會關閉。 因此，如果檔案原開啟為檔案控制代碼或檔案描述項，並使用 `fclose` 關閉，請勿也呼叫 `_close` 關閉檔案描述項；請勿呼叫 Win32 函式 `CloseHandle` 關閉檔案控制代碼。  
  
 `fclose` 和 `_fcloseall` 包含程式碼，保護不受其他執行緒的干擾。 如需非鎖定版本的 `fclose`，請參閱 `_fclose_nolock`。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`fclose`|\<stdio.h>|  
|`_fcloseall`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [fopen](../../c-runtime-library/reference/fopen-wfopen.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_fdopen、_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)
