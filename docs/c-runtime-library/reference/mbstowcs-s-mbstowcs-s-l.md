---
title: "mbstowcs_s、_mbstowcs_s_l | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- _mbstowcs_s_l
- mbstowcs_s
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28f038c1529c2f7fb7bbc28127ee5b528474e0f0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s、_mbstowcs_s_l
將多位元組字元序列轉換成對應的寬字元序列。 這些是 [mbstowcs、_mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `pReturnValue`  
 已轉換的字元數。  
  
 [輸出] `wcstr`  
 所產生之已轉換寬字元字串的緩衝區位址。  
  
 [輸入] `sizeInWords`  
 `wcstr` 緩衝區的大小 (以字組為單位)。  
  
 [in]`mbstr`  
 以 Null 結束之多位元組字元序列的位址。  
  
 [輸入] `count`  
 儲存在 `wcstr` 緩衝區的寬字元數目上限，不包括結束 Null 或 [_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 [輸入] `locale`  
 要使用的地區設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為零，如果失敗，則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|---------------------|------------------------------|  
|`wcstr` 為 `NULL` 且 `sizeInWords` > 0|`EINVAL`|  
|`mbstr` 是 `NULL`|`EINVAL`|  
|目的緩衝區太小，無法包含已轉換的字串 (除非 `count` 是 `_TRUNCATE`；請參閱下面的＜備註＞)|`ERANGE`|  
|`wcstr` 不是 `NULL` 且 `sizeInWords` == 0|`EINVAL`|  
  
 如果發生上述任何一種情況，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會傳回錯誤碼，並將 `errno` 設為如表中所示。  
  
## <a name="remarks"></a>備註  
 `mbstowcs_s` 函式會將 `wcstr` 所指向的多位元組字元字串，轉換成儲存在緩衝區中由 `mbstr` 所指向的寬字元。 除非遇到下列情況之一，否則會繼續為每個字元進行轉換：  
  
-   遇到多位元組的 null 字元  
  
-   遇到無效的多位元組字元  
  
-   儲存在 `wcstr` 緩衝區的寬字元數目等於 `count`。  
  
 目的字串一律會以 Null 結束 (即使發生錯誤亦然)。  
  
 如果 `count` 是特殊值 [_TRUNCATE](../../c-runtime-library/truncate.md)，則 `mbstowcs_s` 會盡量轉換符合目的緩衝區的字串量，同時仍留出空間給 Null 結束字元。  
  
 如果 `mbstowcs_s` 成功轉換來源字串，則會將包括 Null 結束字元在內之轉換後的字串大小 (寬字元)，放入 `*pReturnValue` (假設 `pReturnValue` 不是 `NULL`)。 即使 `wcstr` 引數為 `NULL`，且可讓您決定所需的緩衝區大小，也會發生這種情況。 請注意，如果 `wcstr` 為 `NULL`，則會略過 `count`，且 `sizeInWords` 必須是 0。  
  
 如果 `mbstowcs_s` 遇到無效的多位元組字元，則會將 0 放入 `*pReturnValue`，將目的緩衝區設定為空字串，將 `errno` 設定為 `EILSEQ`，並傳回 `EILSEQ`。  
  
 如果 `mbstr` 和 `wcstr` 所指向的序列重疊，`mbstowcs_s` 的行為不明。  
  
> [!IMPORTANT]
>  確定 `wcstr` 和 `mbstr` 沒有重疊，而且 `count` 正確反映要轉換的多位元組字元數。  
  
 `mbstowcs_s` 會針對任何與地區設定相關的行為使用目前的地區設定，`_mbstowcs_s_l` 與其相同，只不過它會改用傳入的地區設定。 如需詳細資訊，請參閱 [Locale](../../c-runtime-library/locale.md)。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`mbstowcs_s`|\<stdlib.h>|  
|`_mbstowcs_s_l`|\<stdlib.h>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen、mblen、_mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、_mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、_wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、_wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)