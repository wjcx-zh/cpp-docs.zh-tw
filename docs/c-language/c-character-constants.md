---
title: "C 字元常數 | Microsoft Docs"
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
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
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
ms.openlocfilehash: 9c814bfa3e1ef529e12cc159eb3ff91df0941dc8
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="c-character-constants"></a>C 字元常數
「字元常數」是藉由將可代表字元集中的單一字元包含在單引號 (**' '**) 內所形成。 字元常數用於代表[執行字元集](../c-language/execution-character-set.md)內的字元。  
  
## <a name="syntax"></a>語法  
 *character-constant*：  
 **'** *c-char-sequence* **'**  
  
 **L'** *c-char-sequence* **'**  
  
 *c-char-sequence*：  
 *c-char*  
  
 *c-char-sequence c-char*  
  
 *c-char*：  
 來源字元集的所有成員，但單引號 (**'**)、反斜線 (**\\**) 或新行字元除外  
  
 *escape-sequence*  
  
 *escape-sequence*：  
 *simple-escape-sequence*  
  
 *octal-escape-sequence*  
  
 *hexadecimal-escape-sequence*  
  
 *simple-escape-sequence*：下列其中一個  
 **\a \b \f \n \r \t \v**  
  
 **\\' \\" \\\ \\?**  
  
 *octal-escape-sequence*：  
 **\\**  *octal-digit*  
  
 **\\**  *octal-digit octal-digit*  
  
 **\\**  *octal-digit octal-digit octal-digit*  
  
 *hexadecimal-escape-sequence*：  
 **\x**  *hexadecimal-digit*  
  
 *hexadecimal-escape-sequence hexadecimal-digit*  
  
## <a name="see-also"></a>另請參閱  
 [C 常數](../c-language/c-constants.md)
