---
title: "_ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbcl2"
  - "_ismbcl1"
  - "_ismbcl0"
  - "_ismbcl2_l"
  - "_ismbcl1_l"
  - "_ismbcl0_l"
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
  - "ismbcl0"
  - "_ismbcl1_l"
  - "_ismbcl0"
  - "ismbcl1"
  - "ismbcl0_l"
  - "_ismbcl2_l"
  - "ismbcl2"
  - "ismbcl1_l"
  - "_ismbcl1"
  - "_ismbcl0_l"
  - "_ismbcl2"
  - "ismbcl2_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ismbcl0 函式"
  - "_ismbcl0_l 函式"
  - "_ismbcl1 函式"
  - "_ismbcl1_l 函式"
  - "_ismbcl2 函式"
  - "_ismbcl2_l 函式"
  - "ismbcl0 函式"
  - "ismbcl0_l 函式"
  - "ismbcl1 函式"
  - "ismbcl1_l 函式"
  - "ismbcl2 函式"
  - "ismbcl2_l 函式"
ms.assetid: ee15ebd1-462c-4a43-95f3-6735836d626a
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _ismbcl0、_ismbcl0_l、_ismbcl1、_ismbcl1_l、_ismbcl2、_ismbcl2_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Code Page 932 Specific functions**，使用目前的地區設定或指定的 LC\_CTYPE 轉換狀態分類。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbcl0(  
   unsigned int c   
);  
int _ismbcl0_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcl1(  
   unsigned int c   
);  
int _ismbcl1_l(  
   unsigned int c ,  
   _locale_t locale  
);  
int _ismbcl2(  
   unsigned int c   
);  
int _ismbcl2_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 待測試字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。  如果 `c`\< \= 255 且有個對應 `_ismbb`  常式 \(例如， `_ismbcalnum`  對應於 `_ismbbalnum`\)，則結果為對應的 `_ismbb` 方法的傳回值。  
  
## 備註  
 這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
|常式|測試條件 \(唯獨字碼頁 932\)|  
|--------|------------------------|  
|`_ismbcl0`|JIS 非漢字:0x8140\=\<`c`\<\=0x889E。|  
|`_ismbcl0_l`|JIS 非漢字:0x8140\=\<`c`\<\=0x889E。|  
|`_ismbcl1`|JIS 層級 1:0x889F\=\<`c`\<\=0x9872。|  
|`_ismbcl1_l`|JIS 層級 1:0x889F\=\<`c`\<\=0x9872。|  
|`_ismbcl2`|JIS 層級 2:0x989F\=\<`c`\<\=0xEAA4。|  
|`_ismbcl2_l`|JIS 層級 2:0x989F\=\<`c`\<\=0xEAA4。|  
  
 函數檢查指定值 `c` 是否符合上表中說明的測試條件，但是不檢查 `c` 是有效的多位元組字元。  如果低位元組範圍 0x00 – 0x3F、0x7F 或 0xFD – 0xFF，這些函式會傳回非零的值，表示字元符合測試條件。  使用 [\_ismbbtrail](../../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md) 測試多位元組字元是否已定義。  
  
 **結束字碼頁 932 詳情**  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbcl0`|\<mbstring.h\>|  
|`_ismbcl0_l`|\<mbstring.h\>|  
|`_ismbcl1`|\<mbstring.h\>|  
|`_ismbcl1_l`|\<mbstring.h\>|  
|`_ismbcl2`|\<mbstring.h\>|  
|`_ismbcl2_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)