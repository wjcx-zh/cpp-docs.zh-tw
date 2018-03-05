---
title: "類型轉換 (C) | Microsoft Docs"
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
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b1e4dede1dab1fcaf9ae4de5846539924d0095e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="type-conversions-c"></a>類型轉換 (C)
類型轉換取決於指定的運算子以及運算元或運算子的類型。 下列情況會執行類型轉換：  
  
-   將某一類型的值指派給另一個類型的變數，或者運算子在執行運算之前轉換其運算元的類型時  
  
-   將某一類型的值明確轉換為不同的類型時  
  
-   將值當作引數傳遞至函式，或者從函式傳回類型時  
  
 只要是可以使用整數的運算式，皆可使用字元、短整數或整數位元欄位 (無論是否有帶正負號) 或屬於列舉類型的物件。 如果 `int` 可以代表原始類型的所有值，則會將該值轉換為 `int`；否則會將該值轉換為 `unsigned int`。 這個程序稱為「整數提升」。 整數提升會保留值。 也就是，保證提升後的值會和提升之前一樣。 如需詳細資訊，請參閱[一般算術轉換](../c-language/usual-arithmetic-conversions.md)。  
  
## <a name="see-also"></a>請參閱  
 [運算式和指派](../c-language/expressions-and-assignments.md)