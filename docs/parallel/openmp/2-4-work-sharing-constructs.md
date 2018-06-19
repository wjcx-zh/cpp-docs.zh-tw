---
title: 2.4 工作共用建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c00eb94055f26954a283a6172f69228804832ac4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689632"
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共用的建構
工作共用建構會發生這個情形的團隊成員之間相關聯的陳述式執行。 工作共用指示詞不會啟動新的執行緒，並在項目到工作共用建構函式沒有隱含的屏障。  
  
 序列工作共用建構和**屏障**遇到指示詞必須是相同的小組中每個執行緒。  
  
 OpenMP 定義下列的工作共用建構，以及這些詳述於以下各節：  
  
-   **如**指示詞  
  
-   **區段**指示詞  
  
-   **單一**指示詞