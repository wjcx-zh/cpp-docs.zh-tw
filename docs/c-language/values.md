---
title: "值 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13f497358ae320263fd7043787abb943f760809b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="values"></a>值
**ANSI 3.1.2.5**：各種浮點數類型值的表示方式和集合  
  
 **float** 類型包含 32 個位元：1 個位元表示正負號、8 個位元表示指數，23 個位元則表示尾數。 其範圍是 +/-3.4E38，且具有至少 7 位數的整數位數。  
  
 **double** 類型包含 64 個位元：1 個位元表示正負號、11 個位元表示指數，52 個位元則表示尾數。 其範圍是 +/- 1.7E308，且具有至少 15 位數的整數位數。  
  
 **long double** 類型包含 80 個位元：1 個位元表示正負號、15 個位元表示指數，64 個位元則表示尾數。 其範圍是 +/-1.2E4932，且具有至少 19 位數的整數位數。 請注意，在 Microsoft C 編譯器中，**long double** 類型與 **double** 類型的表示方式完全相同。  
  
## <a name="see-also"></a>另請參閱  
 [浮點數學](../c-language/floating-point-math.md)