---
title: _isatty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isatty
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
- _isatty
dev_langs:
- C++
helpviewer_keywords:
- isatty function
- character device checking
- _isatty function
- checking character devices
ms.assetid: 9f1b2e87-0cd7-4079-b187-f2b7ca15fcbe
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 39e8b9520672c676ffec470ab2e89fccdfaf3442
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="isatty"></a>_isatty
判斷檔案描述元是否與字元裝置相關聯。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _isatty(  
int fd   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 參照至需要測試之裝置的檔案描述元。  
  
## <a name="return-value"></a>傳回值  
 如果描述元與字元裝置相關聯，則 `_isatty` 傳回非零值。 否則，`_isatty` 會傳回 0。  
  
## <a name="remarks"></a>備註  
 `_isatty` 函式會判斷`fd` 是否與字元裝置 (終端機、主控台、印表機或序列連接埠) 相關聯。  
  
 這個函式會驗證 `fd` 參數。 如果 `fd` 是不正確的檔案指標，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則函式會傳回 0 並將 `errno` 設定為 `EBADF`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_isatty`|\<io.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_isatty.c  
/* This program checks to see whether  
 * stdout has been redirected to a file.  
 */  
  
#include <stdio.h>  
#include <io.h>  
  
int main( void )  
{  
   if( _isatty( _fileno( stdout ) ) )  
      printf( "stdout has not been redirected to a file\n" );  
   else  
      printf( "stdout has been redirected to a file\n");  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
stdout has not been redirected to a file  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)
