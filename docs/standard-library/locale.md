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
ms.openlocfilehash: 708184a6a6a443456f0d70f57b6be17b281ac4f5
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453910"
---
# <a name="ltlocalegt"></a>&lt;locale&gt;

定義樣板類別和函式，C++ 程式可以用來封裝和操作有關數字、貨幣和行事曆資料表示和格式化的不同文化特性慣例，包括字元分類和字串定序的國際化支援。

## <a name="syntax"></a>語法

```cpp
#include <locale>
```

### <a name="functions"></a>函式

|功能|說明|
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

|類別|描述|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|樣板類別，提供用於內部和外部字元編碼之間轉換的 facet。|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Codecvt 類別的基類, 用來定義稱為`result`的列舉型別, 做為 facet 成員函式的傳回型別, 以指示轉換的結果。|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關轉換的文化特性區域特定資訊的擷取。|
|[collate](../standard-library/collate-class.md)|定序樣板類別，提供處理字串排序慣例的 facet。|
|[collate_byname](../standard-library/collate-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的定序 facet 的物件，啟用有關字串排序慣例的文化特性區域特定資訊的擷取。|
|[ctype](../standard-library/ctype-class.md)|樣板類別，提供用於字元分類、大小寫轉換，以及原生字元集和地區設定所用字元集之間轉換的 facet。|
|[ctype\<char>](../standard-library/ctype-char-class.md)|類別, 這是將樣板類別`ctype<CharType>`明確特製化到**char**類型, 描述可以做為地區設定 facet 的物件, 以表示**char**類型字元的各種屬性。|
|[ctype_base](../standard-library/ctype-base-class.md)|ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。|
|[ctype_byname](../standard-library/ctype-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的 ctype facet 的物件，啟用字元分類、大小寫字元轉換，以及原生字元集和地區設定所指定字元集之間的轉換。|
|[locale](../standard-library/locale-class.md)|描述地區設定物件的類別，將特定文化特性資訊封裝做為共同定義特定當地語系化環境的一組 facet。|
|[messages](../standard-library/messages-class.md)|樣板類別，描述可以做為地區設定 facet 的物件，以便從特定地區設定的國際化訊息目錄擷取當地語系化訊息。|
|[messages_base](../standard-library/messages-base-class.md)|基類, 描述訊息目錄的**int**型別。|
|[messages_byname](../standard-library/messages-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的訊息 facet 的物件，啟用當地語系化訊息擷取。|
|[money_base](../standard-library/money-base-class.md)|ctype 類別的基底類別，用來定義用於個別字元或在整個範圍內字元分類或測試的列舉類型。|
|[money_get](../standard-library/money-get-class.md)|範本類別, 描述可做為地區設定 facet 的物件, 以控制**CharType**類型的序列轉換為貨幣值。|
|[money_put](../standard-library/money-put-class.md)|範本類別, 描述可做為地區設定 facet 的物件, 以控制貨幣值轉換為**CharType**類型的序列。|
|[moneypunct](../standard-library/moneypunct-class.md)|樣板類別, 描述可做為地區設定 facet 的物件, 以描述用來表示貨幣輸入欄位或貨幣輸出欄位之**CharType**類型的序列。|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的 moneypunct facet 的物件，啟用貨幣輸入或輸出欄位格式化。|
|[num_get](../standard-library/num-get-class.md)|樣板類別, 描述可做為地區設定 facet 的物件, 以控制**CharType**類型的序列轉換為數值。|
|[num_put](../standard-library/num-put-class.md)|樣板類別, 描述可做為地區設定 facet 的物件, 以控制數值轉換為**CharType**類型的序列。|
|[numpunct](../standard-library/numpunct-class.md)|樣板類別, 描述可以做為本機 facet 的物件, 以描述用來表示數值和布林運算式格式和標點符號相關資訊的**CharType**類型序列。|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|衍生的樣板類別，描述可以做為特定地區設定的 moneypunct facet 的物件，啟用數值和布林運算式格式和標點符號。|
|[time_base](../standard-library/time-base-class.md)|針對樣板類別 time_get 之 facet 提供基底類別的類別，僅定義列舉類型 dateorder 和此類型的數個常數。|
|[time_get](../standard-library/time-get-class.md)|範本類別, 描述可做為地區設定 facet 的物件, 以控制**CharType**類型的序列轉換為時間值。|
|[time_get_byname](../standard-library/time-get-byname-class.md)|衍生的樣板類別, 描述可做為 time_get\< **CharType**, **InputIterator**> 類型之地區設定 facet 的物件。|
|[time_put](../standard-library/time-put-class.md)|樣板類別, 描述可做為地區設定 facet 的物件, 以控制時間值轉換為**CharType**類型的序列。|
|[time_put_byname](../standard-library/time-put-byname-class.md)|衍生的樣板類別, 描述可做為`time_put` **CharType**, **OutputIterator**> 類型\<之地區設定 facet 的物件。|
|[wbuffer_convert 類別](../standard-library/wbuffer-convert-class.md)|描述資料流緩衝區，可控制與位元組資料流緩衝區之間的項目傳輸。|
|[wstring_convert 類別](../standard-library/wstring-convert-class.md)|樣板類別，會執行寬字串與位元組字串之間的轉換。|

## <a name="see-also"></a>另請參閱

[字碼頁](../c-runtime-library/code-pages.md)\
[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
