---
title: "isgraph、iswgraph、_isgraph_l、_iswgraph_l | Microsoft Docs"
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
  - "isgraph"
  - "iswgraph"
  - "_iswgraph_l"
  - "_isgraph_l"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_isgraph_l"
  - "_iswgraph_l"
  - "_ismbcgraph_l"
  - "Isgraph"
  - "_istgraph_l"
  - "_istgraph"
  - "iswgraph"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isgraph_l 函式"
  - "_ismbcgraph_l 函式"
  - "_istgraph 函式"
  - "_istgraph_l 函式"
  - "_iswgraph_l 函式"
  - "isgraph 函式"
  - "istgraph 函式"
  - "iswgraph 函式"
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isgraph、iswgraph、_isgraph_l、_iswgraph_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否表示圖形字元。  
  
## 語法  
  
```  
int isgraph(  
   int c   
);  
int iswgraph(  
   wint_t c   
);  
int _isgraph_l(  
   int c,  
   _locale_t locale  
);  
int _iswgraph_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要測試的整數。  
  
## 傳回值  
 在 `c` 不為空白，而為一個可列印字元的特殊表示時，這些常式會傳回非零值。  在 `c` 不為空白，而是一個可列印字元的特殊表示時，`isgraph` 會傳回非零值。  在 `c` 不為寬字元空白，而為一個可列印的寬字元時，`iswgraph` 會傳回非零值。  每一個這些常式在傳入 `c` 沒有達到測試條件時回傳零。  
  
 尾碼為 `_l` 的這些函式版本與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`isgraph` 和 `_isgraph_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istgraph`|`isgraph`|[\_ismbcgraph](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswgraph`|  
|`_istgraph_l`|`_isgraph_l`|[\_ismbcgraph\_l](../../c-runtime-library/reference/ismbcgraph-functions.md)|`_iswgraph_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isgraph`|\<ctype.h\>|  
|`iswgraph`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isgraph_l`|\<ctype.h\>|  
|`_iswgraph_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)