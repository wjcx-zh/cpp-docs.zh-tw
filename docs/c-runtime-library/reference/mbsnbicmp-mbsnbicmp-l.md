---
title: "_mbsnbicmp、_mbsnbicmp_l | Microsoft Docs"
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
  - "_mbsnbicmp_l"
  - "_mbsnbicmp"
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
  - "_strnicmp"
  - "_wcsnicmp_l"
  - "_mbsnbicmp"
  - "mbsnbicmp"
  - "mbsnbicmp_l"
  - "_tcsnicmp"
  - "_strnicmp_l"
  - "_tcsnicmp_l"
  - "_wcsnicmp"
  - "_mbsnbicmp_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbicmp 函式"
  - "_mbsnbicmp_l 函式"
  - "_strnicmp 函式"
  - "_strnicmp_l 函式"
  - "_tcsnicmp 函式"
  - "_tcsnicmp_l 函式"
  - "_wcsnicmp 函式"
  - "_wcsnicmp_l 函式"
  - "mbsnbicmp 函式"
  - "mbsnbicmp_l 函式"
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbicmp、_mbsnbicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較兩個多位元組字元字串的 `n` 個位元組，並忽略大小寫。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _mbsnbicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### 參數  
 `string1, string2`  
 以 Null 結束的待比較字串。  
  
 `count`  
 要比較的位元組數目。  
  
## 傳回值  
 傳回值表示子字串之間的關聯性。  
  
|傳回值|描述|  
|---------|--------|  
|\< 0|`string1` 子字串小於 `string2` 子字串。|  
|0|`string1` 子字串等於 `string2` 子字串。|  
|\> 0|`string1` 子字串大於 `string2` 子字串。|  
  
 發生錯誤時，`_mbsnbcmp` 會傳回 `_NLSCMPERROR` \(定義於 String.h 和 Mbstring.h 中\)。  
  
## 備註  
 `_mbsnbicmp` 函式最多會對 `count` 和 `string1` 的前 `string2` 個位元組執行序數比較。  系統會將每個字元轉換成小寫來執行比較；`_mbsnbcmp` 是區分大小寫版本的 `_mbsnbicmp`。  如果在比較 `count` 個字元之前任一字串中已達結束的 null 字元，則會結束比較。  如果字串相等，當比較 `count` 個字元之前任一字串中已達結束的 null 字元時，較短的字串為較小者。  
  
 `_mbsnbicmp`  類似於 `_mbsnicmp`，但會比較字串最多 `count` 個位元組，而不是字元。  
  
 包含 ASCII 資料表中介於 'Z' 和 'a' 之間字元 \('\['、'\\'、'\]'、'^'、'\_' 和 '\`'\) 的兩個字串，會根據其大小寫以不同的方式進行比較。  例如，"`ABCDE`" 和 "`ABCD^`" 這兩個字串在進行小寫比較時的比較方式 \("`abcde`" \> "`abcd^`"\)，與進行大寫比較時的比較方式 \("`ABCDE`" \< "`ABCD^`"\) 不同。  
  
 `_mbsnbicmp` 根據目前使用的多[位元組字碼頁](../../c-runtime-library/code-pages.md)來辨識多位元組字元序列。  不受目前地區設定的影響。  
  
 如果 `string1` 或 `string2` 為 null 指標，`_mbsnbicmp` 會叫用無效參數處理常式 \(如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述\)。  如果允許繼續執行，函式會傳回 `_NLSCMPERROR`，並將 `errno` 設為 `EINVAL`。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsnicmp_l`|`_strnicmp_l`|`_mbsnbicmp_l`|`_wcsnicmp_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnbicmp`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md) 的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat、\_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_mbsnbcmp、\_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_stricmp、\_wcsicmp、\_mbsicmp、\_stricmp\_l、\_wcsicmp\_l、\_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)