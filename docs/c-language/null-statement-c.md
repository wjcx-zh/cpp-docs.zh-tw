---
title: "Null 陳述式 (C) | Microsoft Docs"
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
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
caps.latest.revision: 6
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
ms.openlocfilehash: 4a03d50c5c2a80bccd864f7e4d51df4d33169277
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="null-statement-c"></a>Null 陳述式 (C)
「null 陳述式」是一個只包含分號的陳述式，可位於陳述式會出現的任何地方。 當執行 null 陳述式時不會發生任何事。 撰寫 null 陳述式的正確方式為：  
  
## <a name="syntax"></a>語法  
  
```  
  
;  
  
```  
  
## <a name="remarks"></a>備註  
 **do**、**for**、**if** 和 `while` 等陳述式，需要可執行的陳述式以陳述式主體的形式顯示。 在不需要實質性陳述式主體的情況下，null 陳述式就可滿足語法需求。  
  
 如同任何其他的 C 陳述式一樣，您可以在 null 陳述式前面加上標籤。 若要對不是陳述式的項目加上標籤 (例如複合陳述式右邊的大括號)，您可以對 null 陳述式加上標籤，並將其插入項目的前方，可獲得相同的效果。  
  
 這個範例說明 null 陳述式：  
  
```  
for ( i = 0; i < 10; line[i++] = 0 )  
     ;  
```  
  
 在此範例中，**for** 陳述式的迴圈運算式 `line[i++] = 0` 會將 `line` 的前 10 個元素初始化為 0。 由於不需要進一步的陳述式，因此陳述式主體為 null 陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [陳述式](../c-language/statements-c.md)
