---
title: _get_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_osfhandle
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
dev_langs:
- C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ffc65e12c4a9023d0ef649bbf2cb5e8f7e76808
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
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

*fd*  
現有的檔案描述元。  
  
## <a name="return-value"></a>傳回值

如果傳回的作業系統檔案控制代碼*fd*有效。 否則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，則此函數會傳回`INVALID_HANDLE_VALUE`(-1)，並設定`errno`至`EBADF`，表示檔案控制代碼無效。  
  
## <a name="remarks"></a>備註

若要關閉的檔案，其作業系統 (OS) 檔案控制代碼藉由取得`_get_osfhandle`，呼叫[\_關閉](../../c-runtime-library/reference/close.md)上的檔案描述項*fd*。 請勿呼叫`CloseHandle`對這個函式的傳回值。 基礎作業系統檔案控制代碼擁有者是*fd*檔案描述項，且已關閉時`_close`上呼叫*fd*。 如果所擁有的檔案描述項`FILE *`資料流，然後呼叫[fclose](../../c-runtime-library/reference/fclose-fcloseall.md)上`FILE *`資料流關閉的檔案描述項與基礎作業系統檔案控制代碼。 在此情況下，請勿呼叫`_close`上的檔案描述項。
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_get_osfhandle`|\<io.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱

[檔案處理](../../c-runtime-library/file-handling.md)   
[_close](../../c-runtime-library/reference/close.md)   
[_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
[_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
[_open、_wopen](../../c-runtime-library/reference/open-wopen.md)
