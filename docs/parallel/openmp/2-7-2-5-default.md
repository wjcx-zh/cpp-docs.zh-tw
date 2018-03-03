---
title: "2.7.2.5 預設 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c856df07-705c-4ad3-9105-a268dd33e939
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ee328be7f9f0c4876738f8179c26e700c57702c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="2725-default"></a>2.7.2.5 default
**預設**子句可讓使用者以會影響變數的資料共用屬性。 語法**預設**子句如下所示：  
  
```  
default(shared | none)  
```  
  
 指定**default(shared)**相當明確列出每個目前可見的變數在**共用**子句，除非它是**threadprivate**或**cons**`t`-限定。 沒有明確**預設**子句，預設行為是相同如果**default(shared)**所指定。  
  
 指定**default （none)**需要至少下列其中之一必須針對每個參考中的平行建構語彙範圍的變數，則為 true:  
  
-   變數會明確列出建構包含參考的資料共用屬性子句中。  
  
-   平行建構中宣告的變數。  
  
-   變數是**threadprivate**。  
  
-   變數具有**const**-限定型別。  
  
-   變數是迴圈控制變數的**如**迴圈緊接**如**或**平行的**指示詞，以及變數的參考出現在迴圈內.  
  
 指定的變數上**firstprivate**， **lastprivate**，或**減少**括住的指示詞子句會造成該變數的隱含參考封入內容。 這類的隱含參考也受到上面所列的需求。  
  
 只有一個**預設**子句可指定在**平行**指示詞。  
  
 變數的預設資料共用屬性可以使用覆寫**私人**， **firstprivate**， **lastprivate**，**減少**，和**共用**子句，如下列範例所示：  
  
```  
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\  
   private(x)  private(r)  lastprivate(i)  
```