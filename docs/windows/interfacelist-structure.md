---
title: "InterfaceList 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::InterfaceList
dev_langs: C++
helpviewer_keywords: InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9c7c14dc24bf76444b62adb0870b85fac449e67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="interfacelist-structure"></a>InterfaceList 結構
支援 WRL 基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename T,  
   typename U  
>  
struct InterfaceList;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 介面名稱。遞迴清單中的第一個介面。  
  
 `U`  
 介面名稱。遞迴清單中其餘的介面。  
  
## <a name="remarks"></a>備註  
 用來建立介面的遞迴式清單。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|說明|  
|----------|-----------------|  
|`FirstT`|樣板參數的同義字`T`。|  
|`RestT`|樣板參數的同義字`U`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `InterfaceList`  
  
## <a name="requirements"></a>需求  
 **標頭：** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)