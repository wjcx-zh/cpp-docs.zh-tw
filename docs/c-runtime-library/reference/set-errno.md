---
title: _set_errno | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_errno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_errno
- _set_errno
dev_langs: C++
helpviewer_keywords:
- errno global variable
- set_errno function
- _set_errno function
ms.assetid: d338914a-1894-4cf3-ae45-f2c4eb26590b
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e6ff28df1645446e159e4fc3b0658a8b209ba2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="seterrno"></a>_set_errno
設定 `errno` 全域變數的值。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _set_errno(   
   int value   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸入] `value`  
 `errno` 的新值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回零。  
  
## <a name="remarks"></a>備註  
 可能值定義在 Errno.h 中。 此外，請參閱 [errno 常數](../../c-runtime-library/errno-constants.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_set_errno.c  
#include <stdio.h>  
#include <errno.h>  
  
int main()  
{  
   _set_errno( EILSEQ );  
   perror( "Oops" );  
}  
```  
  
```Output  
Oops: Illegal byte sequence  
```  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_set_errno`|\<stdlib.h>|\<errno.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [_get_errno](../../c-runtime-library/reference/get-errno.md)   
 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)