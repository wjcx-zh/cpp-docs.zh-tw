---
title: "strcoll 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strcoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字碼頁, 用於字串比較"
  - "strcoll 函式"
  - "字串比較 [C++], 特定文化特性"
  - "字串 [C++], 依字碼頁比較"
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcoll 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`strcoll` 和 `wcscoll` 函式比較都是根據正在使用中地區設定的字碼頁的 `LC_COLLATE` 類別設定的兩個字串。  每個 `_mbscoll` 函式會根據目前使用中 \+ 多位元組的字碼頁來比較兩個字串。  使用`coll`函式應該只有在目前字碼頁上，字元集順序和字典字元順序存在差異，且這些差異影響到字串比較時，才會使用。  使用對應的 `cmp` 函式只會測試字串是否相等。  
  
### strcoll 函式  
  
|SBCS|Unicode|MBCS|說明|  
|----------|-------------|----------|--------|  
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[\_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|定序兩個字串|  
|[\_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[\_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[\_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|定序兩個字串 \(不區分大小寫\)|  
|[\_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[\_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[\_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|對照兩個字串第 `count` 個字元|  
|[\_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[\_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[\_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|對照兩個字串第 `count`個字元 \(不區分大小寫\)|  
  
## 備註  
 單一位元組字元 \(SBCS\) 版本這些函式 \(`strcoll`、 `stricoll`、 `_strncoll`和 `_strnicoll`\) 根據目前地區設定的 `LC_COLLATE` 分類設定比較 `string1` 和 `string2` 。  這些函式與對應的 `strcmp` 函式的不同之處在於 `strcoll` 函式使用地區設定提供定序序列的字碼頁資訊。  如果字串比較在字元集順序和字典會不同地區設定，應該使用 `strcoll` 函式來取代對應的 `strcmp` 函式。  如需`LC_COLLATE`的詳細資訊，請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)。  
  
 對於某些字碼頁和對應的字元集，字元順序字元集的可能與字典會不同。  在「C」地區設定，這不成立:字元順序在 ASCII 字元集中相同字元的字、編輯纂順序。  例如，然而，在某些歐洲字碼頁字元「a」\(值 0x61\) 以字元「ä」\(值 0xE4\) 在字元集，不過，字元「ä 之前」字一般地在字元「a」之前。  若要執行字典會比較這個執行個體，請使用 `strcoll` 而非 `strcmp`。  或者，您可以在原始字串的 `strxfrm` ，然後在結果字串的 `strcmp` 。  
  
 `strcoll`、 `stricoll`、 `_strncoll`和 `_strnicoll` 是根據正在使用中地區設定的字碼頁會自動處理多位元組字元字串，與其寬字元 \(Unicode\) 對應項目。  這些函式多位元組字元 \(MBCS\) 版本，不過，視目前使用中 \+ 多位元組的字碼頁自動分頁以字元為基礎的字串。  
  
 因為 `coll` 函式 \(以地自動分頁字串比較的，反之， `cmp` 函式來測試字串是否相等， `coll` 函式比對應的 `cmp` 版本慢。  因此，這些`coll`函式應該只有在目前字碼頁上，字元集順序和字典字元順序存在差異，且這些差異影響到字串比較時，才會使用。  
  
## 請參閱  
 [地區設定](../c-runtime-library/locale.md)   
 [字串操作](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [\_mbsnbcoll、\_mbsnbcoll\_l、\_mbsnbicoll、\_mbsnbicoll\_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp、wcscmp、\_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm、wcsxfrm、\_strxfrm\_l、\_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)