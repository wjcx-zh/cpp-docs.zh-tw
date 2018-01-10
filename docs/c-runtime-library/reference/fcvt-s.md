---
title: _fcvt_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fcvt_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fcvt_s
- _fcvt_s
dev_langs: C++
helpviewer_keywords:
- fcvt_s function
- converting floating point, to strings
- floating-point functions, converting number to string
- _fcvt_s function
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9bd77d18f63885aa29f49ce8bd497f935d292e0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fcvts"></a>_fcvt_s
將浮點數轉換為字串。 這是如 [CRT 的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之增強安全性的 [_lfind](../../c-runtime-library/reference/fcvt.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _fcvt_s(   
   char* buffer,  
   size_t sizeInBytes,  
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
template <size_t size>  
errno_t _fcvt_s(   
   char (&buffer)[size],  
   double value,  
   int count,  
   int *dec,  
   int *sign   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `buffer`  
 保留轉換結果之提供的緩衝區。  
  
 [輸入] `sizeInBytes`  
 以位元組為單位的緩衝區大小。  
  
 [輸入] `value`  
 要轉換的數字。  
  
 [輸入] `count`  
 小數點後的小數位數。  
  
 [輸出] `dec`  
 預存小數點位置的指標。  
  
 [輸出] `sign`  
 預存正負號指標的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需這些錯誤的清單，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`buffer`|`sizeInBytes`|value|count|dec|Sign|傳回|`buffer` 中的值|  
|--------------|-------------------|-----------|-----------|---------|----------|------------|-----------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|未修改。|  
|非 `NULL` (指向有效的記憶體)|<=0|any|any|any|any|`EINVAL`|未修改。|  
|any|any|any|any|`NULL`|any|`EINVAL`|未修改。|  
|any|any|any|any|any|`NULL`|`EINVAL`|未修改。|  
  
 **安全性問題**  
  
 如果 `buffer` 不指向有效的記憶體，而且不是 `NULL`，則 `_fcvt_s` 可能會產生存取違規。  
  
## <a name="remarks"></a>備註  
 `_fcvt_s` 函式會將浮點數轉換成以 Null 結束的字元字串。 `value` 參數是要轉換的浮點數。 `_fcvt_s` 會將 `value` 的數字儲存為字串，並在結尾處附加 Null 字元 ('\0')。 `count` 參數會指定小數點後要儲存的位數。 多餘的數字會四捨五入至 `count` 位置。 如果有效位數少於 `count`，則以零填補字串。  
  
 字串中只能儲存數字。 呼叫之後，可從 `dec` 和 `sign` 取得小數點位置和 `value` 的正負號。 `dec` 參數指向整數值，此整數值會提供字串開頭的小數點位置。 零或負整數值表示小數點位於第一位數字的左邊。 參數 `sign` 指向表示 `value` 正負號的整數。 如果 `value` 是正值，則整數設定為 0；如果 `value` 是負值，則整數設定為非零的數字。  
  
 長度 `_CVTBUFSIZE` 的緩衝區足可供任何浮點值使用。  
  
 `_ecvt_s` 和 `_fcvt_s` 之間的差異位於 `count` 參數解譯中。 `_ecvt_s`解譯`count`做為輸出字串中的位數總數和`_fcvt_s`解譯`count`小數點之後位數的數目。  
  
 在 C++ 中，這個函式的使用已由範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函式的偵錯版本會先用 0xFD 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------------|---------------------|---------------------|  
|`_fcvt_s`|\<stdlib.h>|\<errno.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
 **程式庫︰**所有版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
  
```  
// fcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_fcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 120000  
```  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt_s](../../c-runtime-library/reference/ecvt-s.md)   
 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)   
 [_fcvt](../../c-runtime-library/reference/fcvt.md)