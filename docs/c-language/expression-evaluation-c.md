---
title: "運算式評估 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "運算式評估"
  - "運算式 [C++], 評估"
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 運算式評估 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

涉及指派、一元遞增、一元遞減或呼叫函式的運算式可能會產生評估以外的後果 \(副作用\)。  到達「序列點」時，在序列點之前的全部內容 \(包括任何副作用\) 一定會先完成評估，然後才會對序列點之後的任何內容進行評估。  
  
 「副作用」是評估運算式所造成的變更。  每當運算式評估造成變數值變更時，就會發生副作用。  所有指派運算都有副作用。  如果函式呼叫藉由直接指派或透過指標間接指派的方式變更外部可見項目的值，則也可能有副作用。  
  
## 請參閱  
 [運算元和運算式](../c-language/operands-and-expressions.md)