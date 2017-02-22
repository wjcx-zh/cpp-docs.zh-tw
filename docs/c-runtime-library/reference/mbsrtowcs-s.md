---
title: "mbsrtowcs_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbsrtowcs_s"
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
  - "mbsrtowcs_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mbsrtowcs_s 函式"
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# mbsrtowcs_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將目前的地區設定的多位元組字元字串，轉換為寬字元字串的表示。  [mbsrtowcs](../../c-runtime-library/reference/mbsrtowcs.md) 之具有安全性增強功能的版本，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t * wcstr,  
   size_t sizeInWords,  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
);  
template <size_t size>  
errno_t mbsrtowcs_s(  
   size_t * pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char ** mbstr,  
   size_t count,  
   mbstate_t * mbstate  
); // C++ only  
```  
  
#### 參數  
 \[輸出\] `pReturnValue`  
 已轉換的字元數。  
  
 \[輸出\] `wcstr`  
 緩衝區位址，要儲存產生的已轉換寬字元字串。  
  
 \[輸出\] `sizeInWords`  
 `wcstr` 的大小 \(字數\) \(寬字元\)。  
  
 \[in、out\] `mbstr`  
 要轉換的多位元組字元字串位置的間接指標。  
  
 \[in\] `count`  
 儲存在 `wcstr` 緩衝區的寬字元數目上限，不包括結束的 null 或 [\_TRUNCATE](../../c-runtime-library/truncate.md)。  
  
 \[in、out\] `mbstate`  
 `mbstate_t` 轉換狀態物件的指標。  如果此值為 null 指標，會使用靜態內部轉換狀態物件。  因為內部 `mbstate_t` 物件不是安全執行緒，我們建議您一律傳遞您自己的 `mbstate` 參數。  
  
## 傳回值  
 如果轉換成功為零，若失敗則為錯誤碼。  
  
|錯誤狀況|傳回值和 `errno`|  
|----------|------------------|  
|`wcstr` 為 null 指標且 `sizeInWords` \> 0|`EINVAL`|  
|`mbstr` 為 null 指標|`EINVAL`|  
|`mbstr` 間接指向的字串，包含對目前的地區設定無效的多位元組序列。|`EILSEQ`|  
|目的緩衝區太小，無法包含已轉換的字串 \(除非 `count` 是 `_TRUNCATE`；如需詳細資訊，請參閱＜備註＞\)|`ERANGE`|  
  
 如果這些情形的任一情況發生，則會叫用無效參數例外狀況，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，此函式會傳回錯誤碼，並將 `errno` 設為如表中所示。  
  
## 備註  
 `mbsrtowcs_s` 函式會使用 `mbstr` 中所包含的轉換狀態，將 `wcstr` 間接所指向的多位元組字元字串，轉換為儲存在緩衝區中 `mbstate` 所指向的寬字元。  除非遇到下列情況之一，否則會繼續為每個字元進行轉換：  
  
-   遇到多位元組的 null 字元  
  
-   遇到無效的多位元組字元  
  
-   儲存在 `wcstr` 緩衝區的寬字元數目等於 `count`。  
  
 即使發生錯誤，目的地字串 `wcstr` 也永遠以 null 結束，除非 `wcstr` 為 null 指標。  
  
 如果 `count` 是特殊值 [\_TRUNCATE](../../c-runtime-library/truncate.md)，則 `mbsrtowcs_s` 會盡量轉換符合目的緩衝區的字串量，同時仍留出空間給 null 結束字元。  
  
 如果 `mbsrtowcs_s` 成功轉換來源字串，它會將轉換後的字串大小 \(寬字元\) 和 null 結束字元，放入 `*``pReturnValue` \(假設 `pReturnValue` 不是 null 指標\)。  即使 `wcstr` 引數是 null 指標，且可讓您決定所需的緩衝區大小，也會發生這種情況。  請注意，如果 `wcstr` 為 null 指標，`count` 會被忽略。  
  
 如果 `wcstr` 不是 null 指標，並由於達到結束的 null 字元而停止轉換，則會將 null 指標指派給 `mbstr` 所指向的指標物件。  否則會將超過已轉換之最後一個多位元組字元的位址指派給該物件 \(如果有的話\)。  這可讓後續的函式呼叫，從此呼叫的停止處重新啟動轉換。  
  
 如果 `mbstate` 為 null 指標，會使用程式庫內部 `mbstate_t` 轉換狀態靜態物件。  由於此內部靜態物件不是安全執行緒，我們建議您傳遞您自己的 `mbstate` 值。  
  
 如果 `mbsrtowcs_s` 遇到不是目前地區設定中的有效多位元組字元，會將 \-1 放入 `*``pReturnValue`，將目的緩衝區 `wcstr` 設為空字串，將 `errno` 設為 `EILSEQ`，並傳回 `EILSEQ`。  
  
 如果 `mbstr` 和 `wcstr` 所指的序列重疊，則 `mbsrtowcs_s` 的行為是未定義。  `mbsrtowcs_s` 會被目前地區設定的 LC\_TYPE 分類影響。  
  
> [!IMPORTANT]
>  確定 `wcstr` 和 `mbstr` 沒有重疊，而且 `count` 正確反映要轉換的多位元組字元數。  
  
 `mbsrtowcs_s` 函式的重新啟動能力與 [mbstowcs\_s、\_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md) 不同。  針對相同或其他可重新啟動的函式的後續呼叫，轉換狀態會儲存在 `mbstate` 中。  混合使用可重新啟動和不可重新啟動之函式的結果不明。  例如，如果使用 `mbsrlen` 的後續呼叫，而不是使用 `mbslen`，則應用程式應該使用 `mbsrtowcs_s` 而不是 `mbstowcs_s.`。  
  
 C\+\+ 利用多載樣板簡化了此函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以使用較新且安全的對應函式，來自動取代不安全的舊函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## 例外狀況  
 `mbsrtowcs_s` 函式是安全多執行緒，但前提是只要當這個函式正在執行，且 `mbstate` 引數不是 null 指標時，目前執行緒中必須沒有任何函式呼叫 `setlocale`。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`mbsrtowcs_s`|\<wchar.h\>|  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc、\_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs\_s、\_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)