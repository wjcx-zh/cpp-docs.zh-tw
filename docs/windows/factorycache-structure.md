---
title: "FactoryCache 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::FactoryCache
dev_langs: C++
helpviewer_keywords: FactoryCache structure
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0fc48c9a3651e8c5a6609886862c2f73c5707638
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="factorycache-structure"></a>FactoryCache 結構
支援 Windows 執行階段 c + + 樣板程式庫的基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
struct FactoryCache;  
```  
  
## <a name="remarks"></a>備註  
 包含的 class factory 和 wrt 識別已註冊的值或類別的 COM 物件的位置。  
  
## <a name="members"></a>成員  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[FactoryCache::cookie 資料成員](../windows/factorycache-cookie-data-member.md)|包含的值，識別已註冊的 Windows 執行階段或 COM 類別物件，並稍後用來取消註冊物件。|  
|[FactoryCache::factory 資料成員](../windows/factorycache-factory-data-member.md)|指向以 Windows 執行階段或 COM class factory。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `FactoryCache`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)