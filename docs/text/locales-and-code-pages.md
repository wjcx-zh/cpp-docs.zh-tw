---
title: "地區設定和字碼頁 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元集 [C++], 字碼頁"
  - "字元集 [C++], 地區設定"
  - "字碼頁 [C++]"
  - "字碼頁 [C++], 動態變更"
  - "字碼頁 [C++], 地區設定"
  - "慣例 [C++], 國際字元支援"
  - "地區設定 ID [C++]"
  - "地區設定 [C++]"
  - "地區設定 [C++], 關於地區設定"
  - "當地語系化 [C++], 字碼頁"
  - "當地語系化 [C++], 地區設定"
  - "多位元組字碼頁 [C++]"
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# 地區設定和字碼頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

地區設定識別項 \(LocaleID\) 反應特定地理區域的本地慣例和語言。  一種指定語言可以在一個以上的國家\/地區使用，例如巴西和葡萄牙都使用葡萄牙語。  反過來說，一個國家\/地區可能有一種以上的官方語言。  例如，加拿大有兩種語言：英語和法語。  因此，加拿大有兩種不同的地區設定：加拿大英文和加拿大法文。  有些與地區設定相關的類別含有日期格式和貨幣值的顯示格式。  
  
 語言決定文字和日期格式的轉換，而國家\/地區決定地方轉換。  每一種語言都有唯一的對應，以字碼頁 \(Code Page\) 表示，它包括字母以外的其他字元 \(例如標點符號和數字\)。  字碼頁是字元集並且和語言有關。  因此，[locale](../c-runtime-library/locale.md) 是語言、國家\/地區和字碼頁的唯一組合。  地區設定 \(Locale\) 和字碼頁設定可以在 Run Time 藉著呼叫 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 函式進行變更。  
  
 不同語言可能使用不同的字碼頁。  例如，ANSI 字碼頁 1252 是用於英語和大多數歐洲語言，而 ANSI 字碼頁 932 是用於日語漢字。  事實上，所有的字碼頁都分享最低的 128 個字元 \(0x00 到 0x7F\) 的 ASCII 字元集。  
  
 任何單位元組字碼頁 \(Code Page\) 均可表示於表格內 \(包含 256 個項目\)，做為位元組值到字元的對應 \(包含數字和標點符號\) 或圖像 \(Glyph\)。  任何多位元組字碼頁也可以表示為非常大的對字元為雙位元組值表格 \(含 64K 個項目\)。  然而，事實上它通常表示為一個前 256 \(單一位元組\) 個字元的表格和雙位元組值的範圍。  
  
 如需字碼頁的詳細資訊，請參閱[字碼頁](../c-runtime-library/code-pages.md)。  
  
 C 執行階段程式庫有兩種內部字碼頁類型：地區設定和多位元組。  您可以在程式執行時更改目前的字碼頁 \(請參閱 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 和 [\_setmbcp](../c-runtime-library/reference/setmbcp.md) 函式的文件\)。  同時，執行階段程式庫也可以取得和使用作業系統字碼頁的值。  Windows 2000 中，作業系統字碼頁是「系統預設 ANSI」字碼頁。  此字碼頁在程式執行期間是固定的。  
  
 當地區設定字碼頁更改時，與地區設定有關的一組函式的行為會更改為受選定字碼頁指示的行為。  根據預設，所有與地區設定有關的函式都會以對 "C" 地區設定獨特的地區設定字碼頁來開始執行。  您可以藉著呼叫 `setlocale` 函式來更改內部地區設定字碼頁 \(以及其他地區設定特定的屬性\)。  呼叫 `setlocale` \(LC\_ALL, ""\) 可以將地區設定設為作業系統使用者地區設定所指定的值。  
  
 同樣的，當多位元字碼頁變更時，多位元組函式的行為更改成選定字碼頁所指定的。  根據預設，所有多位元組函式都會以對應於作業系統的預設字碼頁的多位元組字碼頁來開始執行。  您可以藉著呼叫 `_setmbcp` 函式來更改內部多位元組字碼頁。  
  
 C 執行階段函式 `setlocale` 可以設定、變更或查詢某些或所有目前程式的地區設定資訊。  [\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) 常式是 `setlocale` 的寬字元版；`_wsetlocale` 的引數和傳回值都是寬字元字串。  
  
## 請參閱  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [字元集移植性的優點](../text/benefits-of-character-set-portability.md)