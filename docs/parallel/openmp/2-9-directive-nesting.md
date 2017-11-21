---
title: "2.9 指示詞的巢狀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f1af9f515861863af5906c99d78aa66d08aa09b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="29-directive-nesting"></a>2.9 巢狀使用指示詞
動態巢狀指示詞必須遵守下列規則：  
  
-   A**平行**動態內的另一個指示詞**平行**邏輯上會建立新的小組，目前的執行緒所組成，除非巢狀平行處理原則已啟用。  
  
-   **如**，**區段**，和**單一**繫結至相同的指示詞**平行**不允許在彼此進行巢狀。  
  
-   **重大**具有相同名稱的指示詞不能在彼此進行巢狀。 請注意這項限制不足以避免死結。  
  
-   **如**，**區段**，和**單一**動態的範圍中不允許指示詞**重大**，**排序**，和**主要**如果指示詞繫結至相同的區域**平行**為區域。  
  
-   **屏障**動態的範圍中不允許指示詞**如**，**排序**，**區段**，**單一**，**主要**，和**重大**如果指示詞繫結至相同的區域**平行**為區域。  
  
-   **主要**動態的範圍中不允許指示詞**如**，**區段**，和**單一**指示詞如果**master**指示詞繫結至相同**平行**為工作共用指示詞。  
  
-   **排序**動態的範圍中不允許指示詞**重大**如果指示詞繫結至相同的區域**平行**為區域。  
  
-   在平行區域外執行時，允許動態執行平行區域內的任何指示詞，也允許。 執行時以動態方式在使用者指定的平行區域外，指示詞的執行方式只有主要執行緒所組成一個小組。