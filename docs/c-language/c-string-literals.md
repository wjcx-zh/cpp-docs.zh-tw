---
title: "C 字串常值 | Microsoft Docs"
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
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
caps.latest.revision: 11
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
ms.openlocfilehash: 2ca39273bff41d1a08d078445ddf8d8b56252db8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="c-string-literals"></a>C 字串常值
「字串常值」是以雙引號 (**" "**) 括住、來自來源字元集的一連串字元。 字串常值用於表示代表一連串字元，結合在一起會構成 Null 結束字串。 寬字串常值的前面一律要加上字母 **L**。  
  
## <a name="syntax"></a>語法  
 *string-literal*:  
 **"** *s-char-sequence* opt**"**  
  
 **L"** *s-char-sequence* opt**"**  
  
 *s-char-sequence*:  
 *s-char*  
  
 *s-char-sequence s-char*  
  
 *s-char*:  
 來源字元集的所有成員，但雙引號 (")、反斜線 (\\) 或新行字元除外  
  
 *escape-sequence*  
  
 下列範例是簡單的字串常值：  
  
```  
char *amessage = "This is a string literal.";  
```  
  
 [逸出序列](../c-language/escape-sequences.md)表中列出的所有逸出代碼在字串常值中都是有效的。 若要在字串常值中表示雙引號，請使用逸出序列 **\\"**。 單引號 (**'**) 可以不使用逸出序列表示。 反斜線 (**\\**) 出現在字串內時，後面必須接著第二條反斜線 (**\\\\**)。 反斜線出現在行尾時，一律解譯為行接續字元。  
  
## <a name="see-also"></a>另請參閱  
 [C 的元素](../c-language/elements-of-c.md)
