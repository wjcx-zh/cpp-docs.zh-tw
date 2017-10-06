---
title: "運算式評估 (C) | Microsoft Docs"
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
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: a24e94fe4a5c89dad40b7253690475d0cc7bd0eb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="expression-evaluation-c"></a>運算式評估 (C)
涉及指派、一元遞增、一元遞減或呼叫函式的運算式可能會產生評估以外的後果 (副作用)。 到達「序列點」時，在序列點之前的全部內容 (包括任何副作用) 一定會先完成評估，然後才會對序列點之後的任何內容進行評估。  
  
 「副作用」是評估運算式所造成的變更。 每當運算式評估造成變數值變更時，就會發生副作用。 所有指派運算都有副作用。 如果函式呼叫藉由直接指派或透過指標間接指派的方式變更外部可見項目的值，則也可能有副作用。  
  
## <a name="see-also"></a>另請參閱  
 [運算元和運算式](../c-language/operands-and-expressions.md)
