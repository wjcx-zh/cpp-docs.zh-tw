---
title: "後置運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
caps.latest.revision: 7
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 2d456c0eb3add4fbcb7c968d3309625157922051
ms.lasthandoff: 04/01/2017

---
# <a name="postfix-operators"></a>後置運算子
後置運算子在運算式評估時具有最高優先順序 (具有更緊密的繫結)。  
  
## <a name="syntax"></a>語法  
 *postfix-expression*：  
 *primary-expression*  
  
 *postfix-expression*  **[**  *expression*  **]**  
  
 *postfix-expression*  **(**  *argument-expression-list* opt**)**  
  
 *postfix-expression*  **.**  *identifier*  
  
 *postfix-expression*  **->**  *identifier*  
  
 *postfix-expression*  **++**  
  
 *postfix-expression*  **--**  
  
 此優先順序層級的運算子為陣列註標、函式呼叫、結構和等位成員，以及後置遞增和遞減運算子。  
  
## <a name="see-also"></a>另請參閱  
 [C 運算子](../c-language/c-operators.md)
