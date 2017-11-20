---
title: "AsyncResultType 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncResultType
dev_langs: C++
helpviewer_keywords: AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 32cb9a76a9415fc051faf11ecd3268d461297450
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 列舉
指定 GetResults() 方法所傳回的結果類型。  
  
## <a name="syntax"></a>語法  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>值  
  
|名稱|說明|  
|----------|-----------------|  
|`MultipleResults`|多個結果之間開始狀態，並在呼叫 close （） 之前漸進式呈現的一組。|  
|`SingleResult`|單一結果，會顯示完整的事件發生之後。|  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)