---
title: _get_doserrno | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_doserrno
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
- _get_doserrno
- get_doserrno
dev_langs: C++
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c8eff0ac1a97c9a1d48b82601eb0d6dc0bb8bed0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="getdoserrno"></a>_get_doserrno
在作業系統傳回的錯誤值轉譯為 `errno` 值之前，傳回該錯誤值。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _get_doserrno(   
   int * pValue   
);   
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pValue`  
 要填入 `_doserrno` 全域巨集之目前值的整數的指標。  
  
## <a name="return-value"></a>傳回值  
 若 `_get_doserrno` 成功，會傳回 0；若失敗，則傳回錯誤碼。 如果`pValue`為`NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_doserrno` 全域巨集會先在 CRT 初始化期間設為 0，再開始執行處理序。 此巨集是設定為由會傳回作業系統錯誤的任何系統層級函式呼叫所傳回的作業系統錯誤值，且在執行期間永不重設為 0。 當您撰寫程式碼以檢查函式傳回的錯誤值時，請在函式呼叫之前，先一律使用 [_set_doserrno](../../c-runtime-library/reference/set-doserrno.md) 清除`_doserrno`。 因為其他函式呼叫可能會覆寫 `_doserrno`，因此請在函式呼叫之後立即使用 `_get_doserrno` 檢查值。  
  
 我們建議您針對可攜式錯誤碼使用 [_get_errno](../../c-runtime-library/reference/get-errno.md)，而不是`_get_doserrno`。  
  
 `_doserrno`的可能值於\<errno.h> 中定義。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_get_doserrno`|\<stdlib.h>、\<cstdlib> (C++)|\<errno.h>、\<cerrno> (C++)|  
  
 `_get_doserrno` 是 Microsoft 擴充功能。 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [_set_doserrno](../../c-runtime-library/reference/set-doserrno.md)   
 [errno、_doserrno、_sys_errlist，和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)