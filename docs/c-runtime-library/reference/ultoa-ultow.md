---
title: _ultoa、_ultow | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ultoa
- _ultow
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
- ultot
- ultow
- _ultoa
- _ultow
- _ultot
dev_langs:
- C++
helpviewer_keywords:
- ultot function
- converting integers
- _ultot function
- ultow function
- integers, converting
- _ultow function
- _ultoa function
- converting numbers, to strings
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: ''
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94073b947848199bdc093f959ddceadcb1835f16
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2018
---
# <a name="ultoa-ultow"></a>_ultoa、_ultow
將不帶正負號的長整數轉換為字串。 這些函式已有更安全的版本可供使用，請參閱 [_ultoa_s、_ultow_s](../../c-runtime-library/reference/ultoa-s-ultow-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t (&str)[size],  
   int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `value`  
 要轉換的數字。  
  
 `str`  
 字串結果。  
  
 `radix`  
 `value` 的底數。  
  
## <a name="return-value"></a>傳回值  
 所有這些函式都會傳回 `str` 的指標。 不會傳回錯誤。  
  
## <a name="remarks"></a>備註  
 `_ultoa` 函式會將 `value` 轉換為以 Null 結束的字元字串，並將結果 (最多 33 個位元組) 儲存為 `str`。 不會執行任何溢位檢查。 `radix` 指定的基底`value`;`radix`必須在範圍 2-36。 `_ultow` 是 `_ultoa` 的寬字元版本。  
  
> [!IMPORTANT]
>  若要防止緩衝區溢位，請確定 `str` 緩衝區夠大，足以容納轉換的數字加上尾端的 Null 字元。  
  
 在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_ultoa`|\<stdlib.h>|  
|`_ultow`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 請參閱 [_itoa](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md) 的範例。  
  
## <a name="see-also"></a>另請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [_itoa、_i64toa、_ui64toa、_itow、_i64tow、_ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)