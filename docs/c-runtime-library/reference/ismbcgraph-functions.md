---
title: "_ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbcpunct_l"
  - "_ismbcblank"
  - "_ismbcprint"
  - "_ismbcgraph_l"
  - "_ismbcblank_l"
  - "_ismbcpunct"
  - "_ismbcprint_l"
  - "_ismbcspace_l"
  - "_ismbcspace"
  - "_ismbcgraph"
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
  - "_ismbcspace"
  - "_ismbcgraph"
  - "_ismbcpunct"
  - "ismbcspace_l"
  - "ismbcgraph"
  - "_ismbcgraph_l"
  - "_ismbcprint"
  - "_ismbcspace_l"
  - "ismbcprint"
  - "ismbcgraph_l"
  - "ismbcspace"
  - "ismbcpunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcgraph 函式"
  - "_ismbcgraph_l 函式"
  - "_ismbcprint 函式"
  - "_ismbcprint_l 函式"
  - "_ismbcpunct 函式"
  - "_ismbcpunct_l 函式"
  - "_ismbcspace 函式"
  - "_ismbcspace_l 函式"
  - "ismbcgraph 函式"
  - "ismbcgraph_l 函式"
  - "ismbcprint 函式"
  - "ismbcprint_l 函式"
  - "ismbcpunct 函式"
  - "ismbcpunct_l 函式"
  - "ismbcspace 函式"
  - "ismbcspace_l 函式"
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcgraph、_ismbcgraph_l、_ismbcprint、_ismbcprint_l、_ismbcpunct、_ismbcpunct_l、_ismbcblank、_ismbcblank_l、_ismbcspace、_ismbcspace_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷字元是否為圖形字元、顯示字元、標點符號或空格字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbcgraph(  
   unsigned int c   
);  
int _ismbcgraph_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcprint(  
   unsigned int c   
);  
int _ismbcprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcpunct(  
   unsigned int c  
);  
int _ismbcpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcblank(  
   unsigned int c   
);  
int _ismbcblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcspace(  
   unsigned int c   
);  
int _ismbcspace_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 待判斷的字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。  如果 `c`\< \= 255 且有個對應 `_ismbb`  常式 \(例如， `_ismbcalnum`  對應於 `_ismbbalnum`\)，則結果為對應的 `_ismbb` 方法的傳回值。  
  
 這些函式版本是一樣的，只不過結尾為 `_l` 者與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 備註  
 這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
|常式|測試條件|字碼頁 932 範例|  
|--------|----------|----------------|  
|`_ismbcgraph`|圖形|只有當 `c` 代表任何 ASCII 控制項或片假名可列印字元除了泛空白字元 \( \)的單一位元組時，傳回非零。|  
|`_ismbcprint`|可列印的|只有當 `c` 代表任何 ASCII 控制項或片假名可列印字元除了泛空白字元 \( \)的單一位元組時，傳回非零。|  
|`_ismbcpunct`|標點符號|只有當 `c` 可以是任何 ASCII 或片假名標點符號的單一位元組表示時，傳回非零。|  
|`_ismbcblank`|空格或水平索引標籤|只有當 `c` 為空白字元或水平定位字元：`c`\=0x20 或 `c`\=0x09 時，傳回非零值。|  
|`_ismbcspace`|空白字元|只有當 `c` 是空白字元：`c`\=0x20 或 0x09\=\<`c`\<\=0x0D 時，傳回非零。|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbcgraph`|\<mbstring.h\>|  
|`_ismbcgraph_l`|\<mbstring.h\>|  
|`_ismbcprint`|\<mbstring.h\>|  
|`_ismbcprint_l`|\<mbstring.h\>|  
|`_ismbcpunct`|\<mbstring.h\>|  
|`_ismbcpunct_l`|\<mbstring.h\>|  
|`_ismbcblank`|\<mbstring.h\>|  
|`_ismbcblank_l`|\<mbstring.h\>|  
|`_ismbcspace`|\<mbstring.h\>|  
|`_ismbcspace_l`|\<mbstring.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
  
-   [System::Char::IsPunctuation](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)  
  
-   [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
-   對於 `_ismbcgraph` 和 `_ismbcprint`：不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)