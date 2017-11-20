---
title: "格式規格欄位：scanf 和 wscanf 函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- wscanf
- scanf
dev_langs: C++
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 55d92c5e162541b2b805074740d542a52866c48a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>格式規格欄位：scanf 和 wscanf 函式
這裡的資訊適用於整個 `scanf` 系列函式，包括安全的版本，並會說明所用符號，通知 `scanf` 函式如何將輸入資料流 (例如 `scanf` 的輸入資料流 `stdin`) 剖析為插入至程式變數中的值。  
  
 格式規格的格式如下︰  
  
 `%`[`*`] [[寬度](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][類型](../c-runtime-library/scanf-type-field-characters.md)  
  
 `format` 引數會指定輸入的解譯，並可包含下列一或多個項目︰  
  
-   空白字元︰空白 (' ')、定位點 ('\t') 或新行字元 ('\n')。 空白字元會使得 `scanf` 讀取 (但不儲存) 輸入中的所有連續空格字元，一直到下一個非空白字元。 格式中一個空格字元會比對輸入中任何數字 (包括 0) 和空白字元的組合。  
  
-   不含百分比符號 (`%`) 的非空白字元。 非空白字元會使得 `scanf` 讀取 (但不儲存) 符合的非空白字元。 如果輸入資料流中的下一個字元不符合，`scanf` 即終止。  
  
-   格式規格，由百分比符號 (`%`) 引入。 格式規格會使得 `scanf` 讀取，並將輸入字元轉換成指定類型的值。 值會指派給引數清單中的引數。  
  
 格式為從左讀到右。 預期格式規格外的字元會比對輸入資料流中的序列字元，會掃描但不儲存輸入資料流中的符合字元。 如果輸入資料流中的字元與格式規格相衝突，`scanf` 即終止，且該字元會留在輸入資料流中，好像從未被讀取過。  
  
 遇到第一個格式規格時，第一個輸入欄位的值時會根據此規格轉換，並儲存在第一個 `argument` 所指定的位置。 第二個格式規格會讓第二個輸入欄位轉換，並儲存在第二個 `argument` 中，以此類推至格式字串結尾。  
  
 輸入欄位定義為到第一個空白字元 (空格、定位鍵或新行字元)、或根據格式規格無法轉換的第一個字元，或達到欄位寬度 (如指定) 的所有字元。 如果指定的規格有太多引數，額外的引數會予以評估但忽略。 如果提供給格式規格的引數不足，則結果不可預測。  
  
 每個格式規格的欄位都是單一字元，或表示特定格式選項的數字。 `type` 字元出現在最後一個選擇性格式欄位之後，決定將輸入欄位解譯為字元、字串或數字。  
  
 最簡單的格式規格只包含百分比符號和一個 `type` 字元 (例如 `%s`)。 如果百分比符號 (`%`) 後面的字元沒有和格式控制字元一樣的意義，該字元及後續字元 (直到下一個百分比符號) 都視為一般順序的字元，也就是必須符合輸入的字元序列。 例如，指定要輸入百分比符號字元，請使用 `%%`。  
  
 星號 (`*`) 跟在百分比符號後面會抑制指派下一個輸入欄位，解譯為指定類型的欄位。 掃描但不儲存欄位。  
  
 `scanf` 系列函式的安全版本 (具有 `_s` 尾碼的版本)，需要在每個 `c`、`C`、`s`、`S` 或 `[` 類型參數之後，立即傳遞緩衝區大小參數。 如需 `scanf` 函式系列安全版本的詳細資訊，請參閱 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)。  
  
## <a name="see-also"></a>另請參閱  
 [scanf 寬度規格](../c-runtime-library/scanf-width-specification.md)   
 [scanf 類型欄位字元](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)