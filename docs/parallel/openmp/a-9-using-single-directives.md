---
title: "A.9 使用單一指示詞 |Microsoft 文件"
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
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11d41d62448d41d7a11ef747e65cc6ac47e4bd7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a9---using-single-directives"></a>A.9 使用 single 指示詞
下列範例會示範`single`指示詞 ([區段 2.4.3](../../parallel/openmp/2-4-3-single-construct.md)在頁面上 15)。 在範例中，只有一個執行緒 (通常是第一個執行緒所遇到之`single`指示詞) 會列印進度訊息。 使用者必須要將執行的執行緒不做任何假設`single`> 一節。 所有其他執行緒會略過`single`區段，並在結尾處屏障停止`single`建構。 如果其他的執行緒可以繼續執行，而不等候執行緒執行`single` 區段中，`nowait`子句上指定`single`指示詞。  
  
```  
#pragma omp parallel  
{  
    #pragma omp single  
        printf_s("Beginning work1.\n");  
    work1();  
    #pragma omp single  
        printf_s("Finishing work1.\n");  
    #pragma omp single nowait  
        printf_s("Finished work1 and beginning work2.\n");  
    work2();  
}  
```