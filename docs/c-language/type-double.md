---
title: "類型 double | Microsoft Docs"
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
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: aa4e81164a02774f7f9aa034f2c1a5492233600d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="type-double"></a>類型 double
使用 double 類型的雙精確度值有 8 個位元組。 其格式類似於浮點格式，但是它有 11 位額外的 1023 指數和一個 52 位元尾數，再加上隱含的 1 個高序位位元。 若是 double 類型，此格式的範圍大約從 1.7E-308 到 1.7E+308。  
  
 **Microsoft 特定的**  
  
 double 類型包含 64 個位元：1 表示正負號，11 表示指數，52 則表示尾數。 其範圍是 +/-1.7E308，且具有至少 15 位數的整數位數。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)
