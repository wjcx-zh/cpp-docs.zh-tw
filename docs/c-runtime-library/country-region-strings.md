---
title: "國家/地區字串 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 708651f59ceff638482264e3fc57228e8a1822b2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="countryregion-strings"></a>Country/Region Strings
國家/地區字串可以結合語言字串，建立適合 `setlocale`、 `_wsetlocale`、 `_create_locale`和 `_wcreate_locale` 函式的地區設定規格。 如需各種 Windows 作業系統版本支援的國家/地區名稱清單，請參閱[國家語言支援 (NLS) API 參考](http://msdn.microsoft.com/goglobal/bb896001.aspx)。在這些清單中，國家/地區字串可以是 [地區設定 - 語言 (國家/地區)]  欄中的任一國家值，或 [國家或地區名稱縮寫]  欄中的任一縮寫。  
  
 C 執行階段程式庫實作也支援下列其他國家/地區字串和縮寫：  
  
|國家/地區字串|縮寫|對等的地區設定名稱|  
|----------------------------|------------------|----------------------------|  
|美洲|USA|zh-TW|  
|英國|GBR|en-GB|  
|中國|CHN|zh-CN|  
|捷克|CZE|cs-CZ|  
|英國|GBR|en-GB|  
|英國|GBR|en-GB|  
|荷蘭|NLD|nl-NL|  
|香港特別行政區|HKG|zh-HK|  
|紐西蘭|NZL|en-NZ|  
|nz|NZL|en-NZ|  
|中華人民共和國|CHN|zh-CN|  
|pr-china|CHN|zh-CN|  
|波多黎各|PRI|es-PR|  
|斯洛伐克|SVK|sk-SK|  
|南非|ZAF|af-ZA|  
|南韓|KOR|ko-KR|  
|南非|ZAF|af-ZA|  
|南韓|KOR|ko-KR|  
|千里達及托巴哥|TTO|en-TT|  
|uk|GBR|en-GB|  
|英國|GBR|en-GB|  
|美國|USA|zh-TW|  
|us|USA|zh-TW|  
  
## <a name="see-also"></a>另請參閱  
 [地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [語言字串](../c-runtime-library/language-strings.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
