---
title: fsetpos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fsetpos
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
- fsetpos
dev_langs:
- C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 1facc7aec41e7ab1c8b420f6792d76cce0d2b029
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="fsetpos"></a>fsetpos
設定資料流位置指標。  
  
## <a name="syntax"></a>語法  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stream`  
 `FILE` 結構的指標。  
  
 `pos`  
 位置指標儲存區。  
  
## <a name="return-value"></a>傳回值  
 如果成功，`fsetpos` 會傳回 0。 在失敗時，此函式會傳回非零值，並設定 `errno` 為下列其中一項資訊清單常數 (定義於 ERRNO.H 中)：`EBADF`，這表示檔案不可存取或 `stream` 指向的物件不是有效的檔案結構；或 `EINVAL`，這表示針對 `stream` 或 `pos` 傳遞了無效的值。 如果傳入無效參數，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `fsetpos`函式會將檔案位置指標`stream`值`pos`，在先前的呼叫，以取得`fgetpos`針對`stream`。 清除檔案結尾指標的函式，並復原任何影響[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)上`stream`。 呼叫 `fsetpos` 之後，`stream` 上的下一項作業可能是輸入或輸出。  
  
## <a name="requirements"></a>需求  
  
|函式|必要的標頭|  
|--------------|---------------------|  
|`fsetpos`|\<stdio.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
 請參閱 [fgetpos](../../c-runtime-library/reference/fgetpos.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [資料流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)
