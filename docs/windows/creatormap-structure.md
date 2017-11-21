---
title: "CreatorMap 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs: C++
helpviewer_keywords: CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c61238a809da49686975acbfb8016996cf5d5c1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="creatormap-structure"></a>CreatorMap 結構
支援 Windows 執行階段 c + + 樣板程式庫的基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>備註  
 包含如何初始化、 註冊及取消註冊物件的相關資訊。  
  
 CreatorMap 包含下列資訊：  
  
-   如何初始化、 註冊及取消註冊物件。  
  
-   比較傳統的 COM 或 Windows 執行階段 factory 根據啟用資料的方式。  
  
-   介面的處理站快取和伺服器名稱的相關資訊。  
  
## <a name="members"></a>Members  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CreatorMap::activationId 資料成員](../windows/creatormap-activationid-data-member.md)|代表透過傳統的 COM 類別識別碼或 Windows 執行階段名稱識別的物件識別碼。|  
|[CreatorMap::factoryCache 資料成員](../windows/creatormap-factorycache-data-member.md)|CreatorMap 存放處理站快取的指標。|  
|[CreatorMap::factoryCreator 資料成員](../windows/creatormap-factorycreator-data-member.md)|建立指定 CreatorMap factory。|  
|[CreatorMap::serverName 資料成員](../windows/creatormap-servername-data-member.md)|儲存 CreatorMap 的伺服器名稱。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CreatorMap`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)