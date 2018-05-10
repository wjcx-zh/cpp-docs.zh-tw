---
title: 2.6.1 master 建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a60a8df380fdcc0052d8fe2d070c8d926bcb28f8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="261-master-construct"></a>2.6.1 master 建構
**主要**指示詞會識別指定的結構化的區塊由小組主要執行緒執行的建構。 語法**主要**指示詞時，如下所示：  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 在小組中的其他執行緒不會執行相關聯的結構化的區塊。 沒有隱含的屏障項目，或從 master 建構結束。