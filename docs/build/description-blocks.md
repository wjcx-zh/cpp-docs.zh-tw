---
title: "描述區塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 37f095f5ae46e4b555f1d3f7996bd5f357e58ee2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="description-blocks"></a>描述區塊
描述區塊是以相依性 （選擇性） 後面接著命令區塊：  
  
```  
targets... : dependents...  
    commands...  
```  
  
 相依性一行指定一個或多個目標和零個或多個相依項目。 目標必須是該行的開頭。 允許來自相依項目以冒號 （:） 的個別目標，則為空格或定位字元。 若要分割線，請使用反斜線 (\) 之後的目標或相依性。 如果目標不存在，有較早的時間戳記比相依性，或為[虛擬目標](../build/pseudotargets.md)，NMAKE 執行的命令。 如果相依性為目標，這樣其他位置並不存在或對自身的相依性而言已過期，NMAKE 就會更新相依之前更新目前的相依性。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
 [目標](../build/targets.md)  
  
 [相依性](../build/dependents.md)  
  
## <a name="see-also"></a>請參閱  
 [NMAKE 參考](../build/nmake-reference.md)