---
title: "常數摘要 | Microsoft Docs"
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
- constants, C
ms.assetid: 4158234c-e189-4e25-970f-52a04bc6380a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e46966d56084a615ffdf2763adefbcd1e416a6ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-constants"></a>常數摘要
`constant`：  
 *floating-point-constant*  
  
 *integer-constant*  
  
 *enumeration-constant*  
  
 *character-constant*  
  
 *floating-point-constant*：  
 *fractional-constant exponent-part* opt*floating-suffix* opt  
  
 *digit-sequence exponent-part floating-suffix* opt  
  
 *fractional-constant*：  
 *digit-sequence* opt**.***digit-sequence*  
  
 *digit-sequence*  **.**  
  
 *exponent-part*：  
 **e**  *sign* opt*digit-sequence*  
  
 **E**  *sign* opt*digit-sequence*  
  
 *sign*：下列其中一個  
 **+ -**  
  
 *digit-sequence*：  
 *digit*  
  
 *digit-sequence digit*  
  
 *floating-suffix*：下列其中一個  
 **f l F L**  
  
 *integer-constant*：  
 *decimal-constant integer-suffix* opt  
  
 *octal-constant integer-suffix* opt  
  
 *hexadecimal-constant integer-suffix* opt  
  
 *decimal-constant*：  
 *nonzero-digit*  
  
 *decimal-constant digit*  
  
 *octal-constant*：  
 **0**  
  
 *octal-constant octal-digit*  
  
 *hexadecimal-constant*：  
 **0x**  *hexadecimal-digit*  
  
 **0X**  *hexadecimal-digit*  
  
 *hexadecimal-constant hexadecimal-digit*  
  
 *nonzero-digit*：下列其中一個  
 **1 2 3 4 5 6 7 8 9**  
  
 *octal-digit*：下列其中一個  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimal-digit*：下列其中一個  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **a b c d e f**  
  
 **A B C D E F**  
  
 *unsigned-suffix*：下列其中一個  
 **u U**  
  
 *long-suffix*：下列其中一個  
 **l L**  
  
 *character-constant*：  
 **'** *c-char-sequence*  
  
 **'L'** *c-char-sequence* **'**  
  
 *integer-suffix*：  
 *unsigned-suffix long-suffix* opt  
  
 *long-suffix unsigned-suffix* opt  
  
 *c-char-sequence*：  
 *c-char*  
  
 *c-char-sequence c-char*  
  
 *c-char*：  
 來源字元集的所有成員，但不包括單引號 (')、反斜線 (**\\**) 或新行字元 *escape-sequence*  
  
 *escape-sequence*：  
 *simple-escape-sequence*  
  
 *octal-escape-sequence*  
  
 *hexadecimal-escape-sequence*  
  
 *simple-escape-sequence*：下列其中一個  
 **\a \b \f \n \r \t \v**  
  
 **\\' \\" \\\ \\?**  
  
 *octal-escape-sequence*：  
 **\\** *octal-digit*  
  
 **\\** *octal-digit octal-digit*  
  
 **\\** *octal-digit octal-digit octal-digit*  
  
 *hexadecimal-escape-sequence*：  
 **\x**  *hexadecimal-digit*  
  
 *hexadecimal-escape-sequence hexadecimal-digit*  
  
## <a name="see-also"></a>請參閱  
 [語彙文法](../c-language/lexical-grammar.md)