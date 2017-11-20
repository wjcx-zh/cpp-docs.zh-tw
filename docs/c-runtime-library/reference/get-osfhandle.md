---
title: _get_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
dev_langs: C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3b15b4577d1d8c0b24df82acff76494474c4e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="getosfhandle"></a>_get_osfhandle

擷取與指定的檔案描述元相關聯的作業系統檔案控制代碼。  
  
## <a name="syntax"></a>語法  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
### <a name="parameters"></a>參數

*fd*的現有檔案描述項。  
  
## <a name="return-value"></a>傳回值

的作業系統檔案控制代碼，如果*fd*有效。 否則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則此函數會傳回`INVALID_HANDLE_VALUE`(-1)，並設定`errno`至`EBADF`，表示檔案控制代碼無效。  
  
## <a name="remarks"></a>備註

若要關閉的檔案，作業系統檔案控制代碼藉由取得`_get_osfhandle`，呼叫[\_關閉](../../c-runtime-library/reference/close.md)上的檔案描述項*fd*。 呼叫 `_close` 也會關閉基礎控制代碼，因此不必在原始控制代碼上呼叫 Win32 函式 `CloseHandle`。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_get_osfhandle`|\<io.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)   
[_close](../../c-runtime-library/reference/close.md)   
[_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
[_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
[_open、_wopen](../../c-runtime-library/reference/open-wopen.md)
