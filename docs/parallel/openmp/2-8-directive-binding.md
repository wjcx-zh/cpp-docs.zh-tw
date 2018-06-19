---
title: 2.8 指示詞繫結 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02492b228b4bb47a800955f078a59ce680312a87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689450"
---
# <a name="28-directive-binding"></a>2.8 指示詞繫結
動態繫結的指示詞必須遵守下列規則：  
  
-   **如**，**區段**，**單一**，**主要**，和**屏障**指示詞繫結至以動態方式封入**平行**，如果有的話，不論任何的值**如果**可能會存在於該指示詞上的子句。 如果目前正在執行任何平行區域，指示詞會不執行由小組，只有主要執行緒所組成。  
  
-   **排序**指示詞繫結至封入動態**如**。  
  
-   **不可部分完成**指示詞會強制執行有關的獨佔存取**不可部分完成**所有執行緒，而不只是目前的小組中的指示詞。  
  
-   **重大**指示詞會強制執行有關的獨佔存取**重大**所有執行緒，而不只是目前的小組中的指示詞。  
  
-   指示詞可以永遠不會繫結至任何外部的最接近的指示詞動態封入**平行**。