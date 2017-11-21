---
title: "money_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocmon/std::money_base
dev_langs: C++
helpviewer_keywords: money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: de697e26d04e9d70cb1bbbdf4ecbf269d6918e4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="moneybase-class"></a>money_base 類別
此類別描述範本類別 [moneypunct](../standard-library/moneypunct-class.md) 之所有特製化通用的列舉和結構。  
  
## <a name="syntax"></a>語法  
```    
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};  
```  
## <a name="remarks"></a>備註  
 **part** 列舉描述結構模式中陣列欄位元素的可能值。 **part** 的值如下：  
  
- **none**：比對零個或多個空格，或不產生任何項目。  
  
- **sign**：比對或產生正負號。  
  
- **space**：比對零個或多個空格，或是產生空格。  
  
- **symbol**：比對或產生貨幣符號。  
  
- **value**：比對或產生貨幣值。  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



