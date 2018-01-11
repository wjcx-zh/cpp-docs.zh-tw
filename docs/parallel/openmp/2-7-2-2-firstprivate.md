---
title: "2.7.2.2 firstprivate |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e4f73b3cb418204008fda9962cf67797c8182f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate
**Firstprivate**子句提供所提供的功能的超集**私人**子句。 語法**firstprivate**子句如下所示：  
  
```  
firstprivate(variable-list)  
```  
  
 中指定的變數*變數清單*有**私人**子句語意，如中所述[區段 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md)在 25 頁面上。 如同它已執行過一次每個執行緒，則建構執行緒的執行前，可發生初始化或建構。 如**firstprivate**平行建構上的子句，新的私用物件的初始值已存在前平行建構之執行緒遇到它的原始物件的值。 如**firstprivate**工作共用建構上的子句，每個執行緒執行的工作共用建構新的私用物件的初始值是時間存在之前的原始物件的值，在相同的執行緒遇到工作共用的建構。 此外，c + + 物件的每個執行緒的新私用物件是複製建構自原始物件。  
  
 若要限制**firstprivate**子句如下：  
  
-   中指定的變數**firstprivate**子句必須沒有不完整的類型或參考類型。  
  
-   指定為類別類型的變數**firstprivate**必須可存取且明確的複製建構函式。  
  
-   變數是在平行區域內的私用或會出現在**減少**子句**平行**指示詞中不能指定**firstprivate**上的子句工作共用指示詞繫結至平行建構。