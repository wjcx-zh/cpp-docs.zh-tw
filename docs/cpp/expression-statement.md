---
title: 運算陳述式 |Microsoft 文件
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
ms.openlocfilehash: 60879ca8792e3259a69b7a9a3de6cd83dce0d6d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="expression-statement"></a>運算陳述式
運算陳述式會造成對於運算式的評估。 運算陳述式不會發生控制權轉移或反覆項目的情形。  
  
 運算陳述式的語法很簡單  
  
## <a name="syntax"></a>語法  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>備註  
 在下一個陳述式執行之前，會完成運算陳述式中所有運算式的評估，以及所有副作用。 最常見的運算陳述式是指派和函式呼叫。  由於運算式是選擇性的單獨的分號會視為空白運算式陳述式，稱為[null](../cpp/null-statement.md)陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 陳述式概觀](../cpp/overview-of-cpp-statements.md)