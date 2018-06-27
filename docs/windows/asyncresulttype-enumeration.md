---
title: AsyncResultType 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de4a8465dd61e52425a0335e171cf516591ae589
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863305"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列舉
指定 GetResults() 方法所傳回的結果類型。  
  
## <a name="syntax"></a>語法  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`MultipleResults`|多個結果之間開始狀態，並在呼叫 close （） 之前漸進式呈現的一組。|  
|`SingleResult`|單一結果，會顯示完整的事件發生之後。|  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)