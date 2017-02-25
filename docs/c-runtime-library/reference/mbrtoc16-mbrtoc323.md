---
title: "mbrtoc16 mbrtoc323 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbrtoc16"
  - "mbrtoc32"
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
  - "mbrtoc16"
  - "mbrtoc32"
  - "uchar/mbrtoc16"
  - "uchar/mbrtoc32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mbrtoc16 函式"
  - "mbrtoc32 函式"
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# mbrtoc16, mbrtoc32
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將窄字串的第一個多位元組字元轉譯為對等的 UTF\-16 或 UTF\-32 字元。  
  
## 語法  
  
```  
size_t mbrtoc16(   
   char16_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
size_t mbrtoc32(  
   char32_t* destination,   
   const char* source,   
   size_t max_bytes,   
   mbstate_t* state   
);  
  
```  
  
#### 參數  
 `destination`  
 `char16_t` 或 `char32_t` 指標，相當於要轉換的多位元組字元。 如果是 null，函式不會儲存值。  
  
 `source`  
 要轉換的多位元組字元字串的指標。  
  
 `max_bytes`  
 `source` 的位元組數目上限，用來檢查是否有要轉換字元。 此值應該介於一與 `source` 中所餘下的位元組數目之間，包括任何 null 結束字元。  
  
 `state`  
 將多位元組字串轉譯成一或多個輸出字元所使用的 `mbstate_t` 轉換狀態物件指標。  
  
## 傳回值  
 成功時會傳回適用條件中第一個條件的值，假設目前的 `state` 值是：  
  
|值|條件|  
|-------|--------|  
|0|下一組數目為 `max_bytes` 以下且轉換自 `source` 的字元與 null 寬字元對應，如果 `destination` 不是 null，就會儲存這個值。<br /><br /> `state` 包含初始移位狀態。|  
|介於 1 和 `max_bytes` \(含\) 之間|傳回的值是完成有效多位元組字元的 `source` 位元組數目。 如果 `destination` 不是 null，就會儲存已轉換的寬字元。|  
|\-3|如果 `destination` 不是 null，因先前的函式呼叫所產生的下一個寬字元就已儲存在 `destination` 中。 這個函式呼叫不會消耗 `source` 任何位元組。<br /><br /> 當 `source` 指向需要多個寬字元來表示的多位元組字元時 \(例如，surrogate 字組\)，就會更新 `state` 值，以便下個函式呼叫寫出額外的字元。|  
|\-2|下一個 `max_bytes` 位元組代表不完整但可能有效的多位元組字元。 沒有任何值儲存於 `destination`。 如果 `max_bytes` 為零就可能發生這個結果。|  
|\-1|發生了編碼錯誤。 後 `max_bytes` 個位元組 \(或更少個位元組\) 不會產生完整且有效的多位元組字元。 沒有任何值儲存於 `destination`。<br /><br /> `EILSEQ` 儲存在 `errno` 中，而轉換狀態 `state` 尚未指定。|  
  
## 備註  
 `mbrtoc16` 函式最多從 `source` 讀取 `max_bytes` 位元組以尋找第一個完整有效的多位元組字元，然後將對等的 UTF\-16 字元儲存在 `destination`。 來源位元組會根據目前執行緒的多位元組地區設定解譯。 如果多位元組字元需要多個 UTF\-16 輸出字元，例如 surrogate 字組，則會設定 `state` 值，使其在下次呼叫 `mbrtoc16` 時，將下一個 UTF\-16字元儲存於 `destination`。`mbrtoc32` 函式相同，但輸出儲存為 UTF\-32 字元。  
  
 如果 `source` 是 null，這些函式會對 `destination` 使用 `NULL` 的引數、對 `source` 使用 `""` 的引數、對 `max_bytes` 使用 `1` 的引數，傳回呼叫產生的對等項。 忽略 `destination` 和 `max_bytes` 傳遞的值。  
  
 如果 `source` 不是 null，函式會從字串開頭開始檢查到 `max_bytes` 位元組，判斷完成下一個多位元組字元所需要的位元組數目，包括任何移位序列。 如果檢查的位元組包含有效且完整的多位元組字元，函式會將字元轉換成相等的 16 位元或 32 位元寬字元或字元。 如果 `destination` 不是 null，函式會將第一個 \(且可能是唯一\) 結果的字元儲存於目的地。 如果需要其他輸出字元，會在 `state` 設定值，以便後續呼叫讓函式輸出其他字元，並傳回值 \-3。 如果不需要更多輸出字元，則會將 `state` 設為初始移位狀態。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`mbrtoc16`, `mbrtoc32`|\<uchar.h\>|\<cuchar\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [c16rtomb，c32rtomb](../../c-runtime-library/reference/c16rtomb-c32rtomb1.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbsrtowcs](../../c-runtime-library/reference/mbsrtowcs.md)   
 [mbsrtowcs\_s](../../c-runtime-library/reference/mbsrtowcs-s.md)