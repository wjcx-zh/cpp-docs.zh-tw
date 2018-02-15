---
title: _get_fmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_fmode
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
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: abfdd4d9b8838914a91b4db995fcaad573e80829
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="getfmode"></a>_get_fmode
取得檔案 I/O 作業的預設檔案轉譯模式。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pmode`  
 以目前預設模式填滿的整數的指標︰`_O_TEXT`或`_O_BINARY`。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回零；如果失敗，則傳回錯誤碼。 如果`pmode`為`NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，`errno` 會設為 `EINVAL`，且此函式會傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 函式取得 [_fmode](../../c-runtime-library/fmode.md) 全域變數的值。 此變數為低階和資料流檔案 I/O 作業兩者指定預設檔案轉譯模式，例如`_open`、`_pipe`、`fopen`，和`freopen`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_get_fmode`|\<stdlib.h>|\<fcntl.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱 [_set_fmode](../../c-runtime-library/reference/set-fmode.md) 中的範例。  
  
## <a name="see-also"></a>請參閱  
 [_fmode](../../c-runtime-library/fmode.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [文字和二進位模式檔案 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)