---
title: "為您的自訂類別多載 &gt;&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fb029ee7e20a50ef00c2902bda0cca9fb48dbe2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>為您的自訂類別多載 &gt;&gt; 運算子
輸入資料流針對標準類型使用擷取 (`>>`) 運算子。 您可以為您的類別撰寫類似的擷取運算子；成功關鍵取決於是否精確地使用空白字元。  
  
 以下是稍早提供的 `Date` 類別擷取運算子範例：  
  
```  
istream& operator>> (istream& is, Date& dt)  
{  
    is>> dt.mo>> dt.da>> dt.yr;  
    return is;  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [輸入資料流](../standard-library/input-streams.md)

