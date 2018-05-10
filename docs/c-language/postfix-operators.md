---
title: 後置運算子 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a23da2e8ed41954bd6faa2803d6e6c7dfb37a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="postfix-operators"></a>後置運算子
後置運算子在運算式評估時具有最高優先順序 (具有更緊密的繫結)。  
  
## <a name="syntax"></a>語法  
 *postfix-expression*：  
 *primary-expression*  
  
 *postfix-expression*  **[**  *expression*  **]**  
  
 *postfix-expression*  **(**  *argument-expression-list* opt **)**  
  
 *postfix-expression*  **.**  *identifier*  
  
 *postfix-expression*  **->**  *identifier*  
  
 *postfix-expression*  **++**  
  
 *postfix-expression*  **--**  
  
 此優先順序層級的運算子為陣列註標、函式呼叫、結構和等位成員，以及後置遞增和遞減運算子。  
  
## <a name="see-also"></a>請參閱  
 [C 運算子](../c-language/c-operators.md)