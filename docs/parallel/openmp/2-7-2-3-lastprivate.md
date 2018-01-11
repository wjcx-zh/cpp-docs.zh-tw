---
title: "2.7.2.3 lastprivate |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5caf9d870dce301c6055dcb55418b3dbbc3e741f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate
`lastprivate`子句提供所提供的功能的超集`private`子句。 語法`lastprivate`子句如下所示：  
  
```  
lastprivate(variable-list)  
```  
  
 中指定的變數*變數清單*有`private`子句語意。 當`lastprivate`識別工作共用建構，每個值指示詞上出現子句`lastprivate`變數相關聯的迴圈，或以語彙方式最後一個區段指示詞中，依序的最後一個反覆項目指派給變數的原始物件。 無法的變數指派值的最後一個反覆項目**如**或**平行的**，或以語彙方式最後一節**區段**或**平行區段**指示詞，建構後都具有不定值。 未指派的子物件也會建構後具有不定值。  
  
 若要限制`lastprivate`子句如下：  
  
-   所有限制`private`套用。  
  
-   指定為類別類型的變數`lastprivate`必須可存取且明確的複製指派運算子。  
  
-   變數是在平行區域內的私用或會出現在`reduction`子句**平行**指示詞中不能指定`lastprivate`繫結至平行建構工作共用指示詞上的子句。