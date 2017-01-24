---
title: "c16rtomb，c32rtomb | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "c16rtomb"
  - "c32rtomb"
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
  - "c16rtomb"
  - "c32rtomb"
  - "uchar/c16rtomb"
  - "uchar/c32rtomb"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "c16rtomb 函式"
  - "c32rtomb 函式"
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# c16rtomb，c32rtomb
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 UTF\-16 或 UTF\-32 寬字元轉換成目前地區設定的多位元組字元。  
  
## 語法  
  
```  
size_t c16rtomb(  
    char *mbchar,   
    char16_t wchar,  
    mbstate_t *state  
);  
size_t c32rtomb(  
    char *mbchar,   
    char32_t wchar,  
    mbstate_t *state  
);  
```  
  
#### 參數  
 \[輸出\] `mbchar`  
 儲存多位元組轉換字元陣列的指標。  
  
 \[in\] `wchar`  
 要轉換的寬字元。  
  
 \[in、out\] `state`  
 `mbstate_t` 物件的指標。  
  
## 傳回值  
 儲存在陣列物件 `mbchar` 的位元組數目，包括任何移位序列。 如果 `wchar` 不是有效的寬字元，則傳回值 \(`size_t`\)\(\-1\)，`errno` 會設為 `EILSEQ`，而 `state` 值尚未指定。  
  
## 備註  
 `c16rtomb` 函式會將 UTF\-16 字元 `wchar` 轉換成目前地區設定中的對等多位元組窄字元序列。 如果 `mbchar` 不是 null 指標，則函式會將轉換的序列儲存在 `mbchar` 指向的陣列物件中。`mbchar` 最多可儲存 `MB_CUR_MAX` 位元組，而 `state` 設定為產生的多位元組移位狀態。    如果 `wchar` 是 null 寬字元，若有需要，會儲存還原初始移位狀態所需要的序列，後面接著 null 字元，且 `state` 設為初始轉換狀態。`c32rtomb` 函式相同，但轉換 UTF\-32 字元。  
  
 如果 `mbchar` 是 null 指標，此行為相當於呼叫替代 `mbchar` 的內部緩衝區和 `wchar` 的寬 null 字元的函式。  
  
 `state` 轉換狀態物件允許您對這個函式，以及維護多位元組輸出字元移位狀態的其他可重新啟動函式，進行後續呼叫。 當您混合使用可重新啟動但無法重新啟動的函式時，或如果在可重新啟動的函式呼叫之間呼叫 `setlocale` 時，結果未經定義。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`c16rtomb`, `c32rtomb`|C, C\+\+: \<uchar.h\>|  
  
 如需相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtoc16, mbrtoc32](../../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)