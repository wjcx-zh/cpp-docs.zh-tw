---
title: "陳述式摘要 | Microsoft Docs"
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
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
caps.latest.revision: 8
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
ms.openlocfilehash: a3c8b013995688df7647493a5a7be8554da22586
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="summary-of-statements"></a>陳述式摘要
*statement*:  
 *labeled-statement*  
  
 *compound-statement*  
  
 *expression-statement*  
  
 *selection-statement*  
  
 *iteration-statement*  
  
 *jump-statement*  
  
 *try-except-statement* /* Microsoft 特定 \*/  
  
 *try-finally-statement* /* Microsoft 特定 \*/  
  
 *jump-statement*：  
 **goto**  *identifier*  **;**  
  
 **continue ;**  
  
 **break ;**  
  
 **return**  *expression*opt**;**  
  
 *compound-statement*:  
 **{**  *declaration-list*opt*statement-list*opt**}**  
  
 *declaration-list*:  
 *declaration*  
  
 *declaration-list declaration*  
  
 *statement-list*:  
 *statement*  
  
 *statement-list statement*  
  
 *expression-statement*:  
 *expression*opt**;**  
  
 *iteration-statement*：  
 **while (**  *expression*  **)**  *statement*  
  
 **do**  *statement*  **while (**  *expression*  **) ;**  
  
 **for (**  *expression*opt**;** *expression*opt**;** *expression*opt**)** *statement*  
  
 *selection-statement*：  
 **if (**  *expression*  **)**  *statement*  
  
 **if (**  *expression*  **)**  *statement*  **else**  *statement*  
  
 **switch (**  *expression*  **)**  *statement*  
  
 *labeled-statement*：  
 *identifier*  **:**  *statement*  
  
 **case**  *constant-expression*  **:**  *statement*  
  
 **default :**  *statement*  
  
 *try-except-statement*:   /\* Microsoft 特定 \*/  
 **__try**  *compound-statement*  
  
 **__except (**  *expression*  **)**  *compound-statement*  
  
 *try-finally-statement*:   /\* Microsoft 特定 \*/  
 **__try**  *compound-statement*  
  
 **__finally**  *compound-statement*  
  
## <a name="see-also"></a>另請參閱  
 [階段結構文法](../c-language/phrase-structure-grammar.md)
