---
title: "_mbccpy_s、_mbccpy_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbccpy_s
- _mbccpy_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbccpy_s_l
- mbccpy_s_l
- mbccpy_s
- _mbccpy_s
dev_langs: C++
helpviewer_keywords:
- tccpy_s_l function
- _tccpy_s function
- _mbccpy_s function
- mbccpy_s function
- tccpy_s function
- mbccpy_s_l function
- _tccpy_s_l function
- _mbccpy_s_l function
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 942267c2632e6ffafec3d2fa9308bfb3db69aa87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mbccpys-mbccpysl"></a>_mbccpy_s、_mbccpy_s_l
將一個多位元組字元從某個字串複製到另一個字串。 這些是 [_mbccpy、_mbccpy_l](../../c-runtime-library/reference/mbccpy-mbccpy-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _mbccpy_s(  
   unsigned char *dest,  
   size_t buffSizeInBytes,  
   int * pCopied,  
   const unsigned char *src   
);  
errno_t _mbccpy_s_l(  
   unsigned char *dest,  
   size_t buffSizeInBytes,  
   int * pCopied,  
   const unsigned char *src,  
   locale_t locale  
);  
template <size_t size>  
errno_t _mbccpy_s(  
   unsigned char (&dest)[size],  
   int * pCopied,  
   const unsigned char *src   
); // C++ only  
template <size_t size>  
errno_t _mbccpy_s_l(  
   unsigned char (&dest)[size],  
   int * pCopied,  
   const unsigned char *src,  
   locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `dest`  
 複製目的地。  
  
 [輸入] `buffSizeInBytes`  
 目的緩衝區大小。  
  
 [輸出] `pCopied`  
 填入所複製的位元組數目 (若成功，即為 1 或 2)。 如果數目無關緊要，則傳遞 `NULL`。  
  
 [輸入] `src`  
 要複製的多位元組字元。  
  
 [輸入] `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。 如果 `src` 或 `dest` 為 `NULL`，或是 `buffSizeinBytes` 個以上的位元組將會複製到 `dest`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，函式會傳回 `EINVAL`，並將 `errno` 設為 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_mbccpy_s` 函式會將一個多位元組字元從 `src` 複製到 `dest`。 如果 `src` 未指向隱含呼叫 [_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md) 所決定之多位元組字元的前導位元組，則會複製 `src` 所指向的單一位元組。 如果 `src` 指向前導位元組，但下一個位元組為 0 而無效，則會將 0 複製到 `dest`、將`errno` 設定為 `EILSEQ`，且函式會傳回 `EILSEQ`。  
  
 `_mbccpy_s` 不會附加 Null 結束字元；不過，如果 `src` 指向 Null 字元，則會將該 Null 值複製到 `dest` (這只是一般單一位元組複本)。  
  
 填入所複製的位元組數目作為 `pCopied` 中的值。 如果作業成功，可能的值為 1 和 2。 如果傳入 `NULL`，則會略過這個參數。  
  
|`src`|已複製到 `dest`|`pCopied`|傳回值|  
|-----------|----------------------|---------------|------------------|  
|非前導位元組|非前導位元組|1|0|  
|0|0|1|0|  
|後面接著非 0 的前導位元組|後面接著非 0 的前導位元組|2|0|  
|後面接著 0 的前導位元組|0|1|`EILSEQ`|  
  
 請注意，第二個資料列只不過是第一個資料列的特殊案例。 另外請注意，此表格假設 `buffSizeInBytes` >= `pCopied`。  
  
 `_mbccpy_s` 會針對任何與地區設定相關的行為使用目前的地區設定。 `_mbccpy_s_l` 與 `_mbccpy_s` 相同，只不過 `_mbccpy_s_l` 會針對任何與地區設定相關的行為使用傳入的地區設定。  
  
 在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy_s`|巨集或內嵌函式的對應。|`_mbccpy_s`|巨集或內嵌函式的對應。|  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_mbccpy_s`|\<mbstring.h>|  
|`_mbccpy_s_l`|\<mbstring.h>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)