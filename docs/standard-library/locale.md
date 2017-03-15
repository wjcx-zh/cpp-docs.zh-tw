---
title: "&lt;locale&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<locale>"
  - "std.<locale>"
  - "locale/std::<locale>"
  - "std::<locale>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "locale 標頭"
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# &lt;locale&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義樣板類別和函式，C\+\+ 程式可以用來封裝和操作有關數字、貨幣和行事曆資料表示和格式化的不同文化特性慣例，包括字元分類和字串定序的國際化支援。  
  
## 語法  
  
```  
  
#include <locale>  
  
```  
  
### 函式  
  
|||  
|-|-|  
|[has\_facet](../Topic/has_facet.md)|測試特定的 facet 是否在指定的地區設定中儲存。|  
|[isalnum](../Topic/isalnum.md)|測試地區設定中的項目是否為字母或數字字元。|  
|[isalpha](../Topic/isalpha.md)|測試地區設定中的項目是否為字母字元。|  
|[iscntrl](../Topic/iscntrl.md)|測試地區設定中的項目是否為控制字元。|  
|[isdigit](../Topic/isdigit.md)|測試地區設定中的項目是否為數字字元。|  
|[isgraph](../Topic/isgraph.md)|測試地區設定中的項目是否為英數字元或標點符號字元。|  
|[islower](../Topic/islower.md)|測試地區設定中的項目是否為小寫。|  
|[isprint](../Topic/isprint.md)|測試地區設定中的項目是否為可列印的字元。|  
|[ispunct](../Topic/ispunct.md)|測試地區設定中的項目是否為標點符號字元。|  
|[isspace](../Topic/isspace.md)|測試地區設定中的項目是否為空白字元。|  
|[isupper](../Topic/isupper.md)|測試地區設定中的項目是否為大寫。|  
|[isxdigit](../Topic/isxdigit.md)|測試地區設定中的項目是否為用來表示十六進位數字的字元。|  
|[tolower](../Topic/tolower.md)|將字元轉換為小寫。|  
|[toupper](../Topic/toupper.md)|將字元轉換為大寫。|  
|[use\_facet](../Topic/use_facet.md)|傳回儲存在地區設定中指定之類型的 facet 的參考。|  
  
### 類別  
  
|||  
|-|-|  
|[codecvt](../standard-library/codecvt-class.md)|樣板類別，提供用於內部和外部字元編碼之間轉換的 facet。|  
|[codecvt\_base](../standard-library/codecvt-base-class.md)|codecvt 類別的基底類別，用來定義當做 **result** 參考的列舉類型，做為 facet 成員函式的傳回類型以表示轉換結果。|  
|[codecvt\_byname](../standard-library/codecvt-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關轉換的文化特性區域特定資訊的擷取。|  
|[collate](../standard-library/collate-class.md)|定序樣板類別，提供處理字串排序慣例的 facet。|  
|[collate\_byname](../standard-library/collate-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關字串排序慣例的文化特性區域特定資訊的擷取。|  
|[ctype](../standard-library/ctype-class.md)|樣板類別，提供用於字元分類、大小寫轉換，以及原生字元集和地區設定所用字元集之間轉換的 facet。|  
|[ctype\<char\>](../standard-library/ctype-char-class.md)|將樣板類別 **ctype\<CharType**\> 明確特製化為類型 `char` 的類別，描述可以做為地區設定 facet 的物件，表示類型 `char` 之字元各種屬性的特性。|  
|[ctype\_base](../standard-library/ctype-base-class.md)|ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。|  
|[ctype\_byname](../standard-library/ctype-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的 ctype facet 的物件，啟用字元分類、大小寫字元轉換，以及原生字元集和地區設定所指定字元集之間的轉換。|  
|[Locale \- 地區設定](../standard-library/locale-class.md)|描述地區設定物件的類別，將特定文化特性資訊封裝做為共同定義特定當地語系化環境的一組 facet。|  
|[訊息](../standard-library/messages-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以便從特定地區設定的國際化訊息目錄擷取當地語系化訊息。|  
|[messages\_base](../standard-library/messages-base-class.md)|基底類別，描述訊息目錄的 `int` 類型。|  
|[messages\_byname](../standard-library/messages-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的訊息 facet 的物件，啟用當地語系化訊息擷取。|  
|[money\_base](../standard-library/money-base-class.md)|ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。|  
|[money\_get](../standard-library/money-get-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以控制類型 **CharType** 的序列轉換為貨幣值。|  
|[money\_put](../standard-library/money-put-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以控制貨幣值轉換為類型 **CharType** 的序列。|  
|[moneypunct](../standard-library/moneypunct-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以描述用來表示貨幣輸入欄位或貨幣輸出欄位之 **CharType** 類型的序列。|  
|[moneypunct\_byname](../standard-library/moneypunct-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的 moneypunct facet 的物件，啟用貨幣輸入或輸出欄位格式化。|  
|[num\_get](../standard-library/num-get-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以控制類型 **CharType** 的序列轉換為數值。|  
|[num\_put](../standard-library/num-put-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以控制數值轉換為類型 **CharType** 的序列。|  
|[numpunct](../standard-library/numpunct-class.md)|樣板類別，描述可以做為區域 facet 的物件，以描述用來表示數值和布林運算式格式和標點符號資訊之 **CharType** 類型的序列。|  
|[numpunct\_byname](../standard-library/numpunct-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的 moneypunct facet 的物件，啟用數值和布林運算式格式和標點符號。|  
|[time\_base](../standard-library/time-base-class.md)|針對樣板類別 time\_get 之 facet 提供基底類別的類別，僅定義列舉類型 dateorder 和此類型的數個常數。|  
|[time\_get](../standard-library/time-get-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以控制類型 **CharType** 的序列轉換為時間值。|  
|[time\_get\_byname](../standard-library/time-get-byname-class.md)|衍生的樣板類別，描述可做為類型 time\_get\<**CharType**, **InputIterator**\> 的地區設定 facet 的物件。|  
|[time\_put](../standard-library/time-put-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以控制時間值轉換為類型 **CharType** 的序列。|  
|[time\_put\_byname](../standard-library/time-put-byname-class.md)|衍生的樣板類別，描述可做為類型 `time_put`\<**CharType**, **OutputIterator**\> 的地區設定 facet 的物件。|  
|[wbuffer\_convert 類別](../standard-library/wbuffer-convert-class.md)|描述資料流緩衝區，可控制與位元組資料流緩衝區之間的項目傳輸。|  
|[wstring\_convert 類別](../standard-library/wstring-convert-class.md)|樣板類別，會執行寬字串與位元組字串之間的轉換。|  
  
## 請參閱  
 [字碼頁](../c-runtime-library/code-pages.md)   
 [地區設定名稱、語言和國家\/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)