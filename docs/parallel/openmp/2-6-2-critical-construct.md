---
title: 2.6.2 critical 建構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae7070fcc590307e71b0c34259bcbe1c12200550
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689593"
---
# <a name="262-critical-construct"></a>2.6.2 critical 建構
**重大**指示詞會識別限制為單一執行緒的相關聯的結構化區塊執行一次的建構。 語法**重大**指示詞時，如下所示：  
  
```  
#pragma omp critical [(name)]  new-linestructured-block  
```  
  
 選擇性*名稱*可能用來識別重要區域。 用來識別重要區域的識別項具有外部連結，並與標籤、 標記、 成員和一般識別項所使用的命名空間不同的命名空間中。  
  
 關鍵區域的開頭的執行緒等候，直到沒有其他執行緒正在執行具有相同名稱 （以程式） 的關鍵區域。 所有未命名**重大**指示詞對應到相同的未指定名稱。