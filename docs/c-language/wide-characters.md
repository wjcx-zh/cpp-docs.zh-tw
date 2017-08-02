---
title: "寬字元 | Microsoft Docs"
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
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
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
ms.openlocfilehash: 071d9c22045d18e6c43c5336cad943e05e68d3bb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="wide-characters"></a>寬字元
**ANSI 3.1.3.4** 整數字元常數的值，其中含有多於一個字元，或者含有包括多於一個多位元組字元的寬字元常數  
  
 標準字元常數 'ab' 具有整數值 (int) 0x6162。 當有多個位元組時，先前讀取的位元組會以 **CHAR_BIT** 的值向左位移，且下一個位元組則會使用位元 OR 運算子與低 **CHAR_BIT** 位元比較。 多位元組字元常數的位元組數目不能超過 sizeof (int)，32 位元目標程式碼的值為 4。  
  
 多位元組字元常數會如上述讀取，並使用 `mbtowc` 執行階段函式轉換為寬字元常數。 如果結果不是有效的寬字元常數，將發出錯誤。 在任何情況下，`mbtowc` 函式檢查的位元組數目都只限於 `MB_CUR_MAX` 的值。  
  
## <a name="see-also"></a>另請參閱  
 [字元](../c-language/characters.md)
