---
title: 運算式陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d94acdfff2fdea2cc35d0856940270ba82e131af
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405252"
---
# <a name="expression-statement"></a>運算陳述式
運算陳述式會造成對於運算式的評估。 運算陳述式不會發生控制權轉移或反覆項目的情形。  
  
 運算陳述式的語法很簡單  
  
## <a name="syntax"></a>語法  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>備註  
 在下一個陳述式執行之前，會完成運算陳述式中所有運算式的評估，以及所有副作用。 最常見的運算陳述式是指派和函式呼叫。  由於運算式是選擇性的單獨的分號會被視為空的運算陳述式，稱為[null](../cpp/null-statement.md)陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 陳述式概觀](../cpp/overview-of-cpp-statements.md)