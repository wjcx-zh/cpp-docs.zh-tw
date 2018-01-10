---
title: "2.8 指示詞繫結 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 731c509c0c2f300d7a9d4e39261ffedd1c22a094
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="28-directive-binding"></a>2.8 指示詞繫結
動態繫結的指示詞必須遵守下列規則：  
  
-   **如**，**區段**，**單一**，**主要**，和**屏障**指示詞繫結至以動態方式封入**平行**，如果有的話，不論任何的值**如果**可能會存在於該指示詞上的子句。 如果目前正在執行任何平行區域，指示詞會不執行由小組，只有主要執行緒所組成。  
  
-   **排序**指示詞繫結至封入動態**如**。  
  
-   **不可部分完成**指示詞會強制執行有關的獨佔存取**不可部分完成**所有執行緒，而不只是目前的小組中的指示詞。  
  
-   **重大**指示詞會強制執行有關的獨佔存取**重大**所有執行緒，而不只是目前的小組中的指示詞。  
  
-   指示詞可以永遠不會繫結至任何外部的最接近的指示詞動態封入**平行**。