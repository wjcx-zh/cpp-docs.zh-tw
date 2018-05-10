---
title: C 識別項 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cca0381392a1f7c2f227c3296597dc3c614ae0b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="c-identifiers"></a>C 識別項
「識別項」或「符號」是您在程式中為變數、類型、函式及標籤提供的名稱。 識別項名稱的拼字和大小寫不可以與任何關鍵字相同。 您不能將關鍵字 (C 或 Microsoft) 當做識別項；關鍵字僅保留供特殊使用。 您可以在變數、類型或函式的宣告中指定識別項以建立該識別項。 在此範例中，`result` 是整數變數的識別項，且 `main` 和 `printf` 是函式的是識別項名稱。  
  
```  
#include <stdio.h>  
  
int main()  
{  
    int result;  
  
    if ( result != 0 )  
        printf_s( "Bad file handle\n" );  
}  
```  
  
 一旦宣告之後，您可以在後續的程式陳述式中使用識別項來參考相關的值。  
  
 您可以在 `goto` 陳述式中使用一種稱為陳述式標籤的特殊識別項  (宣告的說明請參閱[宣告和類型](../c-language/declarations-and-types.md)，陳述式標籤的說明請參閱 [goto 和標記陳述式](../c-language/goto-and-labeled-statements-c.md))。  
  
## <a name="syntax"></a>語法  
 *identifier*:  
 *nondigit*  
  
 *identifier nondigit*  
  
 *identifier digit*  
  
 `nondigit`：下列其中一個  
 **_ a b c d e f g h i j k l m n o p q r s t u v w x y z**  
  
 **A B C D E F G H I J K L M N O P Q R S T U V W X Y Z**  
  
 `digit`：下列其中一個  
 **0 1 2 3 4 5 6 7 8 9**  
  
 識別項名稱的第一個字元必須是 `nondigit` (也就是說，第一個字元必須是底線或大寫/小寫字母)。 ANSI 允許外部識別碼的名稱使用六個重要字元，內部 (函式內) 識別項名稱則可使用 31 個重要字元。 外部識別項 (在全域範圍中宣告或以儲存類別 `extern` 宣告的識別項) 可能必須遵守其他命名限制，因為這些識別項必須由其他軟體 (例如連結器) 處理。  
  
 **Microsoft 特定的**  
  
 雖然 ANSI 允許外部識別項名稱包含 6 個重要字元、內部 (函式內) 識別項名稱包含 31 個重要字元，但 Microsoft C 編譯器允許內部或外部識別項名稱使用 247 個字元。 如果您不擔心 ANSI 相容性，可以使用 /H (限制外部名稱的長度) 選項將此預設值修改為較小或較大的數字。  
  
 **結束 Microsoft 特定的**  
  
 C 編譯器會將大寫字母和小寫字母視為不同的字母。 這項功能稱為「區分大小寫」，可讓您建立拼字相同但一個或多個字母大小寫不同的相異識別項。 例如，下列每一個識別項都是唯一的：  
  
```  
add  
ADD  
Add  
aDD  
```  
  
 **Microsoft 特定的**  
  
 請勿選取以兩條底線或一條底線加上一個大寫字母開頭的識別項名稱。 ANSI C 標準允許保留以這些字元組合開頭的識別項名稱，供編譯器使用。 若為檔案層級範圍的識別項，名稱前兩個字元也不應包含底線和小寫字母。 以這些字元開頭的識別項名稱也是保留名稱。 依照慣例，Microsoft 使用的巨集名稱是以一條底線和大寫字母開頭，Microsoft 特定的關鍵字名稱則以兩條底線開頭。 為避免任何命名衝突，請一律選取開頭不是一條或兩條底線的識別項名稱，或者是以底線加大寫字母開頭的名稱。  
  
 **結束 Microsoft 特定的**  
  
 以下是符合 ANSI 或 Microsoft 命名限制的有效識別項範例：  
  
```  
j  
count  
temp1  
top_of_page  
skip12  
LastNum  
```  
  
 **Microsoft 特定的**  
  
 雖然預設原始程式檔中的識別項區分大小寫，但目的檔案中的符號並不區分大小寫。 Microsoft C 會將編譯單位中的識別項視為區分大小寫。  
  
 Microsoft 連結器會區分大小寫。 您必須根據大小寫一致地指定所有的識別項。  
  
 「原始程式碼字元集」是一組可以出現在原始程式檔中的合法字元。 在 Microsoft C 中，原始程式碼字元集是標準 ASCII 字元集。 原始程式碼字元集和執行字元集包含當做逸出序列使用的 ASCII 字元。 如需執行字元集的詳細資訊，請參閱[字元常數](../c-language/c-character-constants.md)。  
  
 **結束 Microsoft 特定的**  
  
 識別項的「範圍」是該識別項在程式中出現的區域，其「連結」則用於判斷其他範圍中的相同名稱是否代表同一個識別項。 [存留期、範圍、可見度和連結](../c-language/lifetime-scope-visibility-and-linkage.md)中會說明這些主題。  
  
## <a name="see-also"></a>請參閱  
 [C 的元素](../c-language/elements-of-c.md)