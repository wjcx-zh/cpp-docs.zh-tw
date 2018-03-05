---
title: "字碼頁 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a0899f5f617fd28d121b85183280bd28fe91ee46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="code-pages"></a>字碼頁
`code page` 是字元集，可包括數字、標點符號和其他字符。 不同語言和地區設定可能會使用不同的字碼頁。 例如，ANSI 字碼頁 1252 用於英文和大部分的歐洲語言；OEM 字碼頁 932 用於日文漢字。  
  
 字碼頁在資料表中可以呈現為字元與單一位元組值或多位元組值的對應。 許多字碼頁都共用 0x00 - 0x7F 範圍內字元的 ASCII 字元集。  
  
 Microsoft 執行階段程式庫使用下列類型的字碼頁：  
  
-   系統預設 ANSI 字碼頁。 根據預設，啟動時，執行階段系統會自動將多位元組字碼頁設定為取自作業系統的系統預設 ANSI 字碼頁。 呼叫：  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     也會將地區設定設定為系統預設 ANSI 字碼頁。  
  
-   地區設定字碼頁。 多個執行階段常式的行為取決於包含地區設定字碼頁的目前地區設定 (如需詳細資訊，請參閱[地區設定相關常式](../c-runtime-library/locale.md))。Microsoft 執行階段程式庫中的所有地區設定相關常式預設都會使用對應至 "C" 地區設定的字碼頁。 在執行階段，您可以變更或查詢與 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 呼叫搭配使用的地區設定字碼頁。  
  
-   多位元組字碼頁。 執行階段程式庫中大部分多位元組字元常式的行為取決於目前多位元組字碼頁設定。 這些常式預設會使用系統預設 ANSI 字碼頁。 在執行階段，您可以分別使用 [_getmbcp](../c-runtime-library/reference/getmbcp.md) 和 [_setmbcp](../c-runtime-library/reference/setmbcp.md) 來查詢和變更多位元組字碼頁。  
  
-   "C" 地區設定是透過 ANSI 所定義，以對應至 C 程式傳統上會執行的地區設定。 "C" 地區設定的字碼頁 ("C" 字碼頁) 對應至 ASCII 字元集。 例如，在 "C" 地區設定中，`islower` 只會針對值 0x61 - 0x7A 傳回 true。 在另一個地區設定中，`islower` 可能會針對這些項目傳回 true 以及該地區設定所定義的其他值。  
  
## <a name="see-also"></a>請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)