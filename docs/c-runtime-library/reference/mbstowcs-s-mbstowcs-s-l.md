---
title: "mbstowcs_s、_mbstowcs_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbstowcs_s_l"
  - "mbstowcs_s"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbstowcs_s_l"
  - "mbstowcs_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbstowcs_s_l 函式"
  - "mbstowcs_s 函式"
  - "mbstowcs_s_l 函式"
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbstowcs_s、_mbstowcs_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換寬字元序列至對應的多位元組字元。  這些是 [mbstowcs、\_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) 的安全性增強版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
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
  
#### 參數  
 \[out\] `pReturnValue`  
 要轉換的字元數。  
  
 \[out\] `wcstr`  
 緩衝區位址產生的轉換寬字元字串。  
  
 \[in\] `sizeInWords`  
 `wcstr` 緩衝區的大小\(以word為單位\)。  
  
 \[in\]`mbstr`  
 空結尾多位元組字元序列的位址。  
  
 \[in\] `count`  
 要儲存的寬字元數目上限在 `wcstr` 緩衝區，不包括結束的 null 字元或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in\] `locale`  
 要使用的地區設定。  
  
## 傳回值  
 若成功則為零，失敗則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|----------|------------------|  
|`wcstr` 為 `NULL` 而 `sizeInWords`\> 為 0|`EINVAL`|  
|`mbstr` 為 `NULL`|`EINVAL`|  
|目的端緩衝區太小無法包含已轉換字串\(除非 `count` 是 `_TRUNCATE` 請參閱 \< 備註 \>\)|`ERANGE`|  
|`wcstr` 不是 `NULL` 且 `sizeInWords` \=\= 0。|`EINVAL`|  
  
 如果其中一個錯誤情況發生，無效的參數叫用例外狀況，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續執行，函式會傳回錯誤碼並如表格中所示設定 `errno` 。  
  
## 備註  
 `mbstowcs_s` 函式轉換被 `mbstr` 指向的多位元組字元成儲存在緩衝區中被 `wcstr` 指向的寬字元。  每個字元的轉換會繼續，直到下列其中一個條件符合：  
  
-   遇到多位元組字元 Null  
  
-   遇到無效的多位元組字元  
  
-   在 `wcstr` 緩衝區中的寬字元數目等於 `count`。  
  
 目的資料永遠以 null 結尾 \(即使在錯誤的情況下\)。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md)，則 `mbstowcs_s` 盡量轉換能放入目的緩衝區的字串，同時保留 null 結束字元的空間。  
  
 如果 `mbstowcs_s` 轉換成功來源字串，它在已轉換字串的寬字元大小，包括 null 結束字元，輸入 `*``pReturnValue` \(提供的 `pReturnValue` 不是 `NULL`\)。  即使 `wcstr` 引數為 `NULL` 並提供方法來判斷所需的緩衝區大小，也會發生這種情況，。  請注意，如果 `wcstr` 是 `NULL`， `count` 會忽略，因此， `sizeInWords` 必須是 0。  
  
 如果 `mbstowcs_s` 遇到無效的多位元組字元，它將 0 放入 `*``pReturnValue`，將目的緩衝區初始化為空字串，將 `errno` 設為 `EILSEQ`，並傳回 `EILSEQ`。  
  
 如果被 `mbstr` 和 `wcstr` 指向的序列重疊， `mbstowcs_s` 行為是未定義。  
  
> [!IMPORTANT]
>  確認 `wcstr` 和 `mbstr` 不重疊，而 `count` 正確反映轉換寬字元的數目。  
  
 `mbstowcs_s` 在區域設定相依的動作時使用任何的區域設定。 `_mbstowcs_s_l` 除了使用傳入的區域設定以外其餘相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`mbstowcs_s`|\<stdlib.h\>|  
|`_mbstowcs_s_l`|\<stdlib.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen、mblen、\_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs、\_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb、\_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)