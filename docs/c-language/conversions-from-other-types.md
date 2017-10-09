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
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: ed56c0c9ab3186200d3cbb47224dedc60adddb2f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

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
