---
title: "簡單指派 (C) | Microsoft Docs"
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
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: a60ec2f6f6466b579f917d02dabc24736c5a2e92
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="simple-assignment-c"></a>簡單指派 (C)
簡單指派運算子會將其右運算元指派給其左運算元。 右運算元的值會轉換為指派運算式的類型，並且取代儲存在左運算元指定之物件中的值。 以指派的轉換規則為準 (請參閱[指派轉換](../c-language/assignment-conversions.md))。  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 在此範例中，`y` 的值會轉換成類型 **double** 並指派給 `x`。  
  
## <a name="see-also"></a>另請參閱  
 [C 指派運算子](../c-language/c-assignment-operators.md)
