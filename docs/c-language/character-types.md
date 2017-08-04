---
title: "字元類型 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: f0f8639e90787ddcc90b7a302f226d305f29dce1
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="character-types"></a>字元類型
整數字元常數之前若未加上字母 **L**，即屬於 `int` 類型。 整數字元常數的值若包含單一字元，即為解譯為整數的字元數值。 例如，字元 `a` 的數值為 97 (十進位) 和 61 (十六進位)。  
  
 在語法上，「寬字元常數」是前面加上字母 **L** 的字元常數。寬字元常數具有類型 `wchar_t`，在 STDDEF.H 標頭檔中定義為整數類型。 例如:   
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 寬字元常數寬度為 16 位元，並且會指定擴充的執行字元集的成員。 寬字元常數可用於以字母表示因為太大而無法以 `char` 表示的字元。 如需有關寬字元的詳細資訊，請參閱[多位元組字元和寬字元](../c-language/multibyte-and-wide-characters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [C 字元常數](../c-language/c-character-constants.md)
