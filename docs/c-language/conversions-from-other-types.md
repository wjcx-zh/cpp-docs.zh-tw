---
title: "從其他類型轉換 | Microsoft Docs"
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
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
caps.latest.revision: 9
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
ms.openlocfilehash: e4a0b8b8a377808a18cc106cd2edeef7ecde4abc
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="conversions-from-other-types"></a>從其他類型轉換
由於 `enum` 值在定義上為 `int` 值，因此與 `enum` 值之間來回轉換的方式與 `int` 類型相同。 對於 Microsoft C 編譯器，整數相當於 **long**。  
  
 **Microsoft 特定的**  
  
 不允許在結構或等位型別之間進行轉換。  
  
 所有值都可以轉換成 `void` 類型，不過這類轉換的結果只能在捨棄運算式值的內容中使用，例如運算陳述式。  
  
 `void` 類型在定義上不具任何值。 因此，它無法轉換成任何其他類型，而其他類型也不能藉由指派轉換成 `void`。 不過，您可以將值明確轉型為 `void` 類型，如[類型轉換](../c-language/type-cast-conversions.md)中所述。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [指派轉換](../c-language/assignment-conversions.md)
