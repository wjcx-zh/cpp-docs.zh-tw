---
title: '&lt;locale&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: ae008ef45e8a6bb57505432f2c931a768d4c8ea4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224795"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

定義類別樣板和函式，c + + 程式可用來封裝和操作有關數值、貨幣和 calendric 資料之表示和格式的不同文化特性慣例，包括字元分類和字串定序的國際化支援。

## <a name="syntax"></a>語法

```cpp
#include <locale>
```

### <a name="functions"></a>函式

|函式|說明|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|測試特定的 facet 是否在指定的地區設定中儲存。|
|[isalnum](../standard-library/locale-functions.md#isalnum)|測試地區設定中的項目是否為字母或數字字元。|
|[isalpha](../standard-library/locale-functions.md#isalpha)|測試地區設定中的項目是否為字母字元。|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|測試地區設定中的項目是否為控制字元。|
|[isdigit](../standard-library/locale-functions.md#isdigit)|測試地區設定中的項目是否為數字字元。|
|[isgraph](../standard-library/locale-functions.md#isgraph)|測試地區設定中的項目是否為英數字元或標點符號字元。|
|[islower](../standard-library/locale-functions.md#islower)|測試地區設定中的項目是否為小寫。|
|[isprint](../standard-library/locale-functions.md#isprint)|測試地區設定中的項目是否為可列印的字元。|
|[ispunct](../standard-library/locale-functions.md#ispunct)|測試地區設定中的項目是否為標點符號字元。|
|[isspace](../standard-library/locale-functions.md#isspace)|測試地區設定中的項目是否為空白字元。|
|[isupper](../standard-library/locale-functions.md#isupper)|測試地區設定中的項目是否為大寫。|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|測試地區設定中的項目是否為用來表示十六進位數字的字元。|
|[tolower](../standard-library/locale-functions.md#tolower)|將字元轉換為小寫。|
|[toupper](../standard-library/locale-functions.md#toupper)|將字元轉換為大寫。|
|[use_facet](../standard-library/locale-functions.md#use_facet)|傳回儲存在地區設定中指定之類型的 facet 的參考。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|類別樣板，提供用來在內部和外部字元編碼之間轉換的 facet。|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Codecvt 類別的基類，用來定義稱為的列舉型別 `result` ，做為 facet 成員函式的傳回型別，以指示轉換的結果。|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|衍生的類別範本，描述可以做為指定地區設定之 collate facet 的物件，可讓您抓取關於轉換的文化特性區域特定資訊。|
|[對照](../standard-library/collate-class.md)|Collate 類別範本，提供處理字串排序慣例的 facet。|
|[collate_byname](../standard-library/collate-byname-class.md)|衍生類別範本，描述可以做為指定地區設定之 collate facet 的物件，可讓您抓取關於字串排序慣例的文化特性區域特定資訊。|
|[ctype](../standard-library/ctype-class.md)|提供 facet 的類別範本，用來分類字元、從大寫和小寫轉換成原生字元集和地區設定所使用的集合。|
|[ctype\<char>](../standard-library/ctype-char-class.md)|類別，它是類別樣板的明確特製化 `ctype<CharType>` 類型 **`char`** ，描述可以做為地區設定 facet 的物件，以表示類型字元的各種屬性 **`char`** 。|
|[ctype_base](../standard-library/ctype-base-class.md)|ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。|
|[ctype_byname](../standard-library/ctype-byname-class.md)|衍生類別範本，描述可做為給定地區設定之 ctype facet 的物件，啟用字元分類，並在大小寫和原生和地區設定指定字元集之間轉換字元。|
|[locale](../standard-library/locale-class.md)|描述地區設定物件的類別，將特定文化特性資訊封裝做為共同定義特定當地語系化環境的一組 facet。|
|[messages](../standard-library/messages-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以便從特定地區設定的國際化訊息目錄中取出當地語系化的訊息。|
|[messages_base](../standard-library/messages-base-class.md)|基類，描述 **`int`** 訊息目錄的類型。|
|[messages_byname](../standard-library/messages-byname-class.md)|衍生類別範本，描述可做為給定地區設定之訊息 facet 的物件，啟用當地語系化訊息的抓取。|
|[money_base](../standard-library/money-base-class.md)|ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。|
|[money_get](../standard-library/money-get-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以控制**CharType**類型的序列轉換為貨幣值。|
|[money_put](../standard-library/money-put-class.md)|類別樣板，描述可做為地區設定 facet 的物件，以控制貨幣值轉換為**CharType**類型的序列。|
|[moneypunct](../standard-library/moneypunct-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以描述用來表示貨幣輸入欄位或貨幣輸出欄位之**CharType**類型的序列。|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|衍生類別範本，描述可做為給定地區設定之 moneypunct facet 的物件，啟用格式化貨幣輸入或輸出欄位。|
|[num_get](../standard-library/num-get-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以控制**CharType**類型的序列轉換為數值。|
|[num_put](../standard-library/num-put-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以控制數值轉換為**CharType**類型的序列。|
|[numpunct](../standard-library/numpunct-class.md)|類別樣板，描述可以做為本機 facet 的物件，以描述用來表示數值和布林運算式格式和標點符號相關資訊的**CharType**類型序列。|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|衍生類別範本，描述可做為給定地區設定之 moneypunct facet 的物件，啟用數值和布林運算式的格式和標點符號。|
|[time_base](../standard-library/time-base-class.md)|類別，做為類別樣板 time_get facet 的基類，只定義列舉類型 dateorder 和此類型的數個常數。|
|[time_get](../standard-library/time-get-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以控制**CharType**類型的序列轉換為時間值。|
|[time_get_byname](../standard-library/time-get-byname-class.md)|衍生類別樣板，描述可做為 time_get 類型之地區設定 facet 的物件 \<**CharType**, **InputIterator**> 。|
|[time_put](../standard-library/time-put-class.md)|類別樣板，描述可以做為地區設定 facet 的物件，以控制時間值轉換為**CharType**類型的序列。|
|[time_put_byname](../standard-library/time-put-byname-class.md)|衍生類別範本，描述可做為類型之地區設定 facet 的物件 `time_put` \<**CharType**, **OutputIterator**> 。|
|[wbuffer_convert 類別](../standard-library/wbuffer-convert-class.md)|描述資料流緩衝區，可控制與位元組資料流緩衝區之間的項目傳輸。|
|[wstring_convert 類別](../standard-library/wstring-convert-class.md)|在寬字元串與位元組字串之間執行轉換的類別樣板。|

## <a name="see-also"></a>另請參閱

[字碼頁](../c-runtime-library/code-pages.md)\
[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
