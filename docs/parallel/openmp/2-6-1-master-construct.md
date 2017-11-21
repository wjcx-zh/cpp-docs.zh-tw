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
ms.openlocfilehash: bff566967749068f9792a98dc3cf2151e4df3d9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="261-master-construct"></a>2.6.1 master 建構
**主要**指示詞會識別指定的結構化的區塊由小組主要執行緒執行的建構。 語法**主要**指示詞時，如下所示：  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 在小組中的其他執行緒不會執行相關聯的結構化的區塊。 沒有隱含的屏障項目，或從 master 建構結束。