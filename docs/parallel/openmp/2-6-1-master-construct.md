---
title: "2.6.1 master 建構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2517e19b49f1314e7432bb265756193ea3bb8f91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="261-master-construct"></a>2.6.1 master 建構
**主要**指示詞會識別指定的結構化的區塊由小組主要執行緒執行的建構。 語法**主要**指示詞時，如下所示：  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 在小組中的其他執行緒不會執行相關聯的結構化的區塊。 沒有隱含的屏障項目，或從 master 建構結束。