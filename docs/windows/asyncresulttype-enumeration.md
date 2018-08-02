---
title: AsyncResultType 列舉 |Microsoft Docs
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
ms.openlocfilehash: 8171c4a57621a4f17a5f0ddb0745faa70fde6524
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465281"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列舉
指定所傳回的結果的型別`GetResults()`方法。  
  
## <a name="syntax"></a>語法  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>成員  
  
### <a name="values"></a>值  
  
|名稱|描述|  
|----------|-----------------|  
|`MultipleResults`|多個結果，以漸進方式之間會顯示一組`Start`狀態，以及之前`Close()`呼叫。|  
|`SingleResult`|單一結果，就會顯示完整的事件發生之後。|  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)