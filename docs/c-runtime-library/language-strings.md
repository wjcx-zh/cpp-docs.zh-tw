---
title: "語言字串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.strings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "語言字串"
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# 語言字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`setlocale` 和 `_create_locale` 函式可以在不使用 Unicode 字碼頁的作業系統使用 Windows NLS 應用程式開發介面支援的語言。  如需由作業系統版本支援的語言清單，請參閱 [國家語言支援 \(NLS\) API 參考](http://msdn.microsoft.com/goglobal/bb896001.aspx)。  語言字串可以是任何支援語言清單的 \[**語言**\] 和 \[**語言名稱縮寫**\] 資料行中的值。  C 執行階段程式庫實作也支援這些語言字串：  
  
|語言字串|同義的地區設定名稱|  
|----------|---------------|  
|美語|en\-US|  
|美式英文|en\-US|  
|美式英文|en\-US|  
|澳大利亞語|en\-AU|  
|比利時語|nl\-BE|  
|加拿大|en\-CA|  
|chh|zh\-HK|  
|池氏|zh\-SG|  
|中文|zh|  
|中文 \- 香港|zh\-HK|  
|簡體中文|zh\-CN|  
|中文 \- 新加坡|zh\-SG|  
|繁體中文|zh\-TW|  
|荷蘭文 \- 比利時|nl\-BE|  
|英文 \- 美國|en\-US|  
|英文 \- 澳洲|en\-AU|  
|英文 \- 貝里斯|en\-BZ|  
|英文\-加拿大|en\-CA|  
|英文 \- 加勒比海|en\-029|  
|英文\-愛爾蘭|en\-IE|  
|英文 \- 牙買加|en\-JM|  
|英文\-紐西蘭|en\-NZ|  
|英文 \- 南非|en\-ZA|  
|英文\-千里達和 多巴哥|en\-TT|  
|英文 \- 英國|en\-GB|  
|英文\-美國|en\-US|  
|English \(US\)|en\-US|  
|法文 \- 比利時|fr\-BE|  
|法文\-加拿大|fr\-CA|  
|法文 \- 盧森堡|fr\-LU|  
|法文\-瑞士|fr\-CH|  
|德文 \- 奧地利|de\-AT|  
|德文 \- 列支敦斯登|de\-LI|  
|德文 \- 盧森堡|de\-LU|  
|德文 \- 瑞士|de\-CH|  
|愛爾蘭英文|en\-IE|  
|義大利\-瑞士|it\-CH|  
|挪威文|no|  
|挪威文 \- 巴克摩|nb\-NO|  
|挪威文 \- 耐諾斯克|nn\-NO|  
|葡萄牙文 \- 巴西|pt\-BR|  
|西班牙文 \- 阿根廷|es\-AR|  
|西班牙文 \- 玻利維亞|es\-BO|  
|西班牙文 \- 智利|es\-CL|  
|西班牙文 \- 哥倫比亞|es\-CO|  
|西班牙文 \- 哥斯大黎加|es\-CR|  
|西班牙文 \- 多明尼加|es\-DO|  
|西班牙文 \- 厄瓜多|es\-EC|  
|西班牙文 \-薩爾瓦多|es\-SV|  
|西班牙文 \- 瓜地馬拉|es\-GT|  
|西班牙文 \- 宏都拉斯|es\-HN|  
|西班牙文 \- 墨西哥|es\-MX|  
|西班牙文 \- 現代|es\-ES|  
|西班牙文 \- 尼加拉瓜|es\-NI|  
|西班牙文 \- 巴拿馬|es\-PA|  
|西班牙文 \- 巴拉圭|es\-PY|  
|西班牙文 \- 秘魯|es\-PE|  
|西班牙文 \- 波多黎各|es\-PR|  
|西班牙文 \- 烏拉圭|es\-UY|  
|西班牙文 \- 委內瑞拉|es\-VE|  
|瑞典文 \- 芬蘭|sv\-FI|  
|瑞士語|de\-CH|  
|uk|en\-GB|  
|us|en\-US|  
|USA|en\-US|  
  
## 請參閱  
 [地區設定名稱、語言和國家\/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [國家\/地區字串](../c-runtime-library/country-region-strings.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)