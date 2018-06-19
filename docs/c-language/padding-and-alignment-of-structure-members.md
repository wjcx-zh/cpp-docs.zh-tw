---
title: 結構成員的填補和對齊 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb090fc283da0a8aa86dac524272d308127059ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32385373"
---
# <a name="padding-and-alignment-of-structure-members"></a>結構成員的填補和對齊
**ANSI 3.5.2.1**：結構成員的填補和對齊，以及位元欄位是否可以跨儲存單位邊界  
  
 結構成員會依其宣告的順序依序儲存：第一個成員具有最低的記憶體位址，最後一個成員則具有最高的記憶體位址。  
  
 每個資料物件都有一個 alignment-requirement。 所有資料 (結構、等位和陣列除外) 的對齊需求不是物件的大小就是目前的封裝大小 (以 /Zp 或 `pack` pragma 指定，以其中較小者為準)。 結構、等位和陣列的對齊需求是其成員的最大對齊需求。 每個物件都會配置一個 offset，因此  
  
 *offset*  `%` *alignment-requirement* `==` 0  
  
 如果整數類資料類型的大小相同，而且下一個位元欄位符合目前配置單位，不需因為位元欄位的一般對齊需求而加上跨越界限，則相鄰的位元欄位會封裝為相同的 1 個、2 個或 4 個位元組配置單位。  
  
## <a name="see-also"></a>請參閱  
 [結構、等位、列舉和位元欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)