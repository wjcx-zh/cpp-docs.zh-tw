---
title: "結構成員的填補和對齊 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c3a87f1277abb9d5cf3b9d87c6713104ba8e108
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="padding-and-alignment-of-structure-members"></a>結構成員的填補和對齊
**ANSI 3.5.2.1**：結構成員的填補和對齊，以及位元欄位是否可以跨儲存單位邊界  
  
 結構成員會依其宣告的順序依序儲存：第一個成員具有最低的記憶體位址，最後一個成員則具有最高的記憶體位址。  
  
 每個資料物件都有一個 alignment-requirement。 所有資料 (結構、等位和陣列除外) 的對齊需求不是物件的大小就是目前的封裝大小 (以 /Zp 或 `pack` pragma 指定，以其中較小者為準)。 結構、等位和陣列的對齊需求是其成員的最大對齊需求。 每個物件都會配置一個 offset，因此  
  
 *offset*  `%` *alignment-requirement* `==` 0  
  
 如果整數類資料類型的大小相同，而且下一個位元欄位符合目前配置單位，不需因為位元欄位的一般對齊需求而加上跨越界限，則相鄰的位元欄位會封裝為相同的 1 個、2 個或 4 個位元組配置單位。  
  
## <a name="see-also"></a>另請參閱  
 [結構、等位、列舉和位元欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)