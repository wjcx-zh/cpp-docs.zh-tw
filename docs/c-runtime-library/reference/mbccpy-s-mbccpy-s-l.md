---
title: "_mbccpy_s、_mbccpy_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbccpy_s"
  - "_mbccpy_s_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbccpy_s_l"
  - "mbccpy_s_l"
  - "mbccpy_s"
  - "_mbccpy_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbccpy_s 函式"
  - "_mbccpy_s_l 函式"
  - "_tccpy_s 函式"
  - "_tccpy_s_l 函式"
  - "mbccpy_s 函式"
  - "mbccpy_s_l 函式"
  - "tccpy_s 函式"
  - "tccpy_s_l 函式"
ms.assetid: b6e965fa-53c1-4ec3-85ef-a1c4b4f2b2da
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# _mbccpy_s、_mbccpy_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製另一個字串的多位元組字元到某個字串。  這些 [\_mbccpy、\_mbccpy\_l](../../c-runtime-library/reference/mbccpy-mbccpy-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
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
  
#### 參數  
 \[out\] `dest`  
 複製目的地。  
  
 \[in\] `buffSizeInBytes`  
 目的端緩衝區的大小。  
  
 \[out\] `pCopied`  
 使用複製的位元組數填滿 \(1 或 2，如果成功的話\)。  如果您不會在乎數字，傳遞 `NULL` 。  
  
 \[in\] `src`  
 要複製的多位元組字元。  
  
 \[in\] `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  如果 `src` 或 `dest` 是 `NULL`，或者，如果超過 `buffSizeinBytes` 個位元組將會複製到 `dest`，然後不正確的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會回傳 `EINVAL` 並將`errno` 設為 `EINVAL`。  
  
## 備註  
 `_mbccpy_s` 函式將 `src` 的多位元組字元複製到 `dest`。  如果未指向多位元組字元的前導位元組 \(如隱含呼叫 `src` 決定對 [\_ismbblead](../../c-runtime-library/reference/ismbblead-ismbblead-l.md)，則為 `src` 所複製的單一位元組。  如果對前導位元組的 `src` 上，但以下位元組是 0 而不正確，則 0 複製到 `dest`， `errno` 設定為 `EILSEQ`函式會傳回 `EILSEQ`。  
  
 `_mbccpy_s` 不附加 null 結束字元;不過，若 `src` 指向 null 字元，該空點會複製到 `dest` \(這是一般的單位元組複製\)。  
  
 `pCopied` 中的值填入複製的位元組數目。  如果作業成功，可能的值為 1 和 2。  如果傳遞 `NULL` ，則會忽略這個參數。  
  
|`src`|複製至 `dest`。|`pCopied`|傳回值|  
|-----------|-----------------|---------------|---------|  
|非前導位元組|非前導位元組|1|0|  
|0|0|1|0|  
|後為非 0 的前導位元組|後為非 0 的前導位元組|2|0|  
|後為 0 的前導位元組|0|1|`EILSEQ`|  
  
 請注意第二行是個特例第一個。  同時也請注意資料表假設  `buffSizeInBytes` \>\= `pCopied`。  
  
 `_mbccpy_s` 會在所有地區設定相依表現方式中使用目前的地區設定。  `_mbccpy_s_l` 與 `_mbccpy_s` 相似，除了`_mbccpy_s_l` 使用傳遞的地區設定為所有地區設定相關行為。  
  
 在 C\+\+ 中，這些函式的使用被簡化為使用樣板多載；使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tccpy_s`|巨集或內嵌函式的對應。|`_mbccpy_s`|巨集或內嵌函式的對應。|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbccpy_s`|\<mbstring.h\>|  
|`_mbccpy_s_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)