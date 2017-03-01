---
title: "Concurrency 命名空間列舉 (AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b9555023e01cb765ca943fcaaf785cdc2b4e2d0d
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-enums-amp"></a>Concurrency 命名空間列舉 (AMP)
|||  
|-|-|  
|[access_type 列舉](#access_type)|[queuing_mode 列舉](#queuing_mode)|  
  
##  <a name="a-nameaccesstypea--accesstype-enumeration"></a><a name="access_type"></a>access_type 列舉  
 用來表示資料的存取權的各種類型的列舉型別。  
  
```  
enum access_type;  
```  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`access_type_auto`|自動選擇最適合`access_type`加速器。|  
|`access_type_none`|專用。 只能存取加速器上，而不是在 CPU 配置。|  
|`access_type_read`|共用。 配置可存取加速器上，而且可以在 CPU 上閱讀。|  
|`access_type_read_write`|共用。 配置可存取加速器上，而且在 CPU 上可寫入。|  
|`access_type_write`|共用。 在配置加速器上存取和讀取與寫入 CPU。|  

  
##  <a name="a-namequeuingmodea--queuingmode-enumeration"></a><a name="queuing_mode"></a>queuing_mode 列舉  
 指定的佇列模式所支援的快速鍵。  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>值  
  
|名稱|說明|  
|----------|-----------------|  
|`queuing_mode_immediate`|佇列的模式，指定的任何命令，例如[parallel_for_each 函式 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)，只要它們傳回給呼叫者傳送到對應的加速器裝置。|  
|`queuing_mode_automatic`|指定命令會排在對應至命令佇列的佇列模式[accelerator_view](accelerator-view-class.md)物件。 命令傳送至裝置時[accelerator_view:: flush](accelerator-view-class.md#flush)呼叫。|   
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)

