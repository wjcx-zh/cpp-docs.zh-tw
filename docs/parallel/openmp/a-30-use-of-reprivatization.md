---
title: "Reprivatization A.30 使用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 26529090-6c39-40f2-b806-e12374d6b5f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b8a6bedad37e9edd70edd014a9dd8f70143bbe5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a30---use-of-reprivatization"></a>A.30 使用重新設為私用
下列範例會示範 reprivatization 的變數。 可以標示為私用變數`private`巢狀指示詞中一次。 它們沒有封入平行區域中的共用。  
  
```  
int i, a;  
...  
#pragma omp parallel private(a)  
{  
  ...  
  #pragma omp parallel for private(a)  
  for (i=0; i<10; i++)  
     {  
       ...  
     }  
}  
```