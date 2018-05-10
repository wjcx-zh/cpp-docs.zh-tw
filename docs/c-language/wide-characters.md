---
title: 寬字元 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf20b58ad9343f1a90f07a7f4c07bccd397a5888
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="wide-characters"></a>寬字元
**ANSI 3.1.3.4** 整數字元常數的值，其中含有多於一個字元，或者含有包括多於一個多位元組字元的寬字元常數  
  
 標準字元常數 'ab' 具有整數值 (int) 0x6162。 當有多個位元組時，先前讀取的位元組會以 **CHAR_BIT** 的值向左位移，且下一個位元組則會使用位元 OR 運算子與低 **CHAR_BIT** 位元比較。 多位元組字元常數的位元組數目不能超過 sizeof (int)，32 位元目標程式碼的值為 4。  
  
 多位元組字元常數會如上述讀取，並使用 `mbtowc` 執行階段函式轉換為寬字元常數。 如果結果不是有效的寬字元常數，將發出錯誤。 在任何情況下，`mbtowc` 函式檢查的位元組數目都只限於 `MB_CUR_MAX` 的值。  
  
## <a name="see-also"></a>請參閱  
 [字元](../c-language/characters.md)