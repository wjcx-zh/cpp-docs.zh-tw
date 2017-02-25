---
title: "_mbsbtype、_mbsbtype_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsbtype_l"
  - "_mbsbtype"
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
  - "mbsbtype"
  - "mbsbtype_l"
  - "_mbsbtype_l"
  - "_mbsbtype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsbtype 函式"
  - "_mbsbtype_l 函式"
  - "mbsbtype 函式"
  - "mbsbtype_l 函式"
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _mbsbtype、_mbsbtype_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

回傳字串裏的位元組型別。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### 參數  
 `mbstr`  
 多位元組字元序列的位址。  
  
 `count`  
 從字串開頭的位移 \(以位元組為單位\)。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_mbsbtype` 和 `_mbsbtype_l` 回傳其表示指定位元組的測試結果之整數值。  下表的表示常值定義於 Mbctype.h 。  
  
|傳回值|Byte 型別|  
|---------|-------------|  
|`_MBC_SINGLE` \(0\)|單一位元組字元。  例如，在字碼頁 932，`_mbsbtype` 會在指定的位元組位於 0x20 \- 0x7E 或 0xA1 \- 0xDF 的範圍時傳回 0。|  
|`_MBC_LEAD` \(1\)|多位元組字元的前導位元組。  例如，在字碼頁 932，`_mbsbtype` 會在指定的位元組位於 0x81 \- 0x9F 或 0xE0 \- 0xFC 的範圍時傳回 1。|  
|`_MBC_TRAIL` \(2\)|多位元組字元的結尾位元組。  例如，在字碼頁 932 ， `_mbsbtype` 會在指定的位元組位於 0x40 \- 0x7E 或 0x80 \- 0xFC 的範圍時回傳 2 。|  
|`_MBC_ILLEGAL` \(–1\)|`NULL` 字串，無效字元，或在 `mbstr` 裏，位元組 `NULL` 在位移 `count` 位元組前先被遇見。|  
  
## 備註  
 `_mbsbtype` 函式判斷在一個多位元組字元字串的位元組型別。  此函式只會在 `count` 裏檢查位移 `mbstr` 位元組並在指定的位元組之前忽略無效的字元。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果輸入字串是 `NULL`，無效參數處理常式會被調用，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，`errno` 會設定為 `EINVAL` 且函式會傳回 `_MBC_ILLEGAL`。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_mbsbtype`|\<mbstring.h\>|\<mbctype.h\>\*|  
|`_mbsbtype_l`|\<mbstring.h\>|\<mbctype.h\>\*|  
  
 \* 的表示常值是用於回傳值。  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用，請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx) 。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)