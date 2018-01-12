---
title: _ecvt_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _ecvt_s
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
- ecvt_s
- _ecvt_s
dev_langs: C++
helpviewer_keywords:
- _ecvt_s function
- ecvt_s function
- numbers, converting
- converting double numbers
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af4b49b0fd0e4de74a3f454a544c07f08c89b81d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ecvts"></a>_ecvt_s
將 `double` 數字轉換為字串。 這是具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述之安全性增強功能的 [_ecvt](../../c-runtime-library/reference/ecvt.md) 版本。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `_Buffer`  
 填入轉換結果的位數字串指標。  
  
 [輸入] `_SizeInBytes`  
 以位元組為單位的緩衝區大小。  
  
 [輸入] `_Value`  
 要轉換的數字。  
  
 [輸入] `_Count`  
 儲存的位數。  
  
 [輸出] `_Dec`  
 儲存的小數點位置。  
  
 [輸出] `_Sign`  
 已轉換數字的正負號。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零。 如果失敗，傳回的值會是錯誤碼。 錯誤碼於 Errno.h 中定義。 如需詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 如果是下表所列的無效參數，則此函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`_Buffer`|`_SizeInBytes`|_Value|_Count|_Dec|_Sign|傳回值|`buffer` 中的值|  
|---------------|--------------------|-------------|-------------|-----------|------------|------------------|-----------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|未修改。|  
|非 `NULL` (指向有效的記憶體)|<=0|any|any|any|any|`EINVAL`|未修改。|  
|any|any|any|any|`NULL`|any|`EINVAL`|未修改。|  
|any|any|any|any|any|`NULL`|`EINVAL`|未修改。|  
  
 **安全性問題**  
  
 如果 `buffer` 不指向有效的記憶體，而且不是 `NULL`，則 `_ecvt_s` 可能會產生存取違規。  
  
## <a name="remarks"></a>備註  
 `_ecvt_s` 函式會將浮點數轉換為字元字串。 `_Value` 參數是要轉換的浮點數。 此函式最多可將 `count` 位數的 `_Value` 儲存為字串，並在結尾處附加 null 字元 ('\0')。 如果 `_Value` 的位數超過 `_Count`，則會將低位數四捨五入。 如果少於 `count` 個位數，則以零填補字串。  
  
 字串中只能儲存數字。 呼叫之後，可從 `_Dec` 和 `_Sign` 取得小數點位置和 `_Value` 的正負號。 `_Dec` 參數指向整數值，並提供字串開頭的小數點位置。 0 或負整數值表示小數點位於第一位數字的左邊。 `_Sign` 參數指向表示已轉換數字正負號的整數。 如果整數值為 0，則數字為正數。 否則，數字為負數。  
  
 長度 `_CVTBUFSIZE` 的緩衝區足可供任何浮點值使用。  
  
 `_ecvt_s` 和 `_fcvt_s` 之間的差異位於 `_Count` 參數解譯中。 `_ecvt_s` 將 `_Count` 解譯為輸出字串的位數總數，而 `_fcvt_s` 將 `_Count` 解譯為小數點後的位數。  
  
 C++ 中，使用這個函式已為範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
 此函式的偵錯版本會先用 0xFD 填滿緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>需求  
  
|功能|必要的標頭|選擇性標頭|  
|--------------|---------------------|---------------------|  
|`_ecvt_s`|\<stdlib.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 12000  
```  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [atof、_atof_l、_wtof、_wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [_fcvt_s](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt_s](../../c-runtime-library/reference/gcvt-s.md)