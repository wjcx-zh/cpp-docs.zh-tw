---
title: 2.7.2.4 共用 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1de0e32e16d889acb8f1339d783bc194b3508dda
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="2724-shared"></a>2.7.2.4 shared
這個子句共用變數出現在*變數清單*小組中的所有執行緒之間。 在小組內的所有執行緒都存取相同的儲存區的**共用**變數。  
  
 語法**共用**子句如下所示：  
  
```  
shared(variable-list)  
```