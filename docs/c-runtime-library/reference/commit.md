---
title: _commit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _commit
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
- _commit
- commit
dev_langs:
- C++
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed5a3f1e8d1f4a122ecf5a66393fa5c1f5c65f1b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="commit"></a>_commit
將檔案直接清除至磁碟。  
  
## <a name="syntax"></a>語法  
  
```  
int _commit(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>參數  
 `fd`  
 參考已開啟檔案的檔案描述項。  
  
## <a name="return-value"></a>傳回值  
 如果已成功將檔案清除至磁碟，`_commit` 會傳回 0。 傳回值-1 表示錯誤。  
  
## <a name="remarks"></a>備註  
 `_commit` 函式會強制作業系統將與 `fd` 相關聯的檔案寫入至磁碟。 這個呼叫確保立即清除指定的檔案，而不是由作業系統自行決定。  
  
 如果 `fd` 是無效檔案描述元，則會叫用無效的參數處理常式 (如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述)。 如果允許繼續執行，此函式會傳回 -1，並將 `errno` 設為 `EBADF`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|----------------------|  
|`_commit`|\<io.h>|\<errno.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [低層級 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_read](../../c-runtime-library/reference/read.md)   
 [_write](../../c-runtime-library/reference/write.md)