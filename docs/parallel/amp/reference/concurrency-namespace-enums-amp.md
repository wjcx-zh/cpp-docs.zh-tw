---
title: "Concurrency 命名空間列舉 (AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs: C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8979ab026d5bf6aef9d0dd8677bf2ec47a8c6142
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency 命名空間列舉 (AMP)
|||  
|-|-|  
|[access_type 列舉](#access_type)|[queuing_mode 列舉](#queuing_mode)|  
  
##  <a name="access_type"></a>access_type 列舉  
 用來表示資料的存取權的各種類型的列舉類型。  
  
```  
enum access_type;  
```  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`access_type_auto`|自動選擇最適合`access_type`快速鍵。|  
|`access_type_none`|專用。 只能存取在加速器上，而不是在 CPU 配置。|  
|`access_type_read`|共用。 在配置在加速器上存取和讀取 CPU 上。|  
|`access_type_read_write`|共用。 配置在加速器上存取，並可在 CPU 上寫入。|  
|`access_type_write`|共用。 在配置加速器上存取和可讀取且可寫入的 CPU 上。|  

  
##  <a name="queuing_mode"></a>queuing_mode 列舉  
 指定的佇列模式所支援的快速鍵。  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`queuing_mode_immediate`|佇列的模式，指定的任何命令，例如[parallel_for_each 函式 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)，因為它們會傳回給呼叫者會傳送至對應的加速器裝置。|  
|`queuing_mode_automatic`|指定命令會排在對應至命令佇列的佇列模式[accelerator_view](accelerator-view-class.md)物件。 命令傳送至裝置時[accelerator_view:: flush](accelerator-view-class.md#flush)呼叫。|   
  
## <a name="see-also"></a>請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
