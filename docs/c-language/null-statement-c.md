---
title: Null 陳述式 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72e120fa412481a8313809bd5cdaf748de498bde
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384264"
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
  
## <a name="see-also"></a>請參閱  
 [陳述式](../c-language/statements-c.md)