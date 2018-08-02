---
title: CreatorMap 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fadba5993b7445af2386f6e0669f210e29560c6c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464252"
---
# <a name="creatormap-structure"></a>CreatorMap 結構
支援的 Windows 執行階段 c + + 樣板程式庫基礎結構，並不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>備註  
 包含如何初始化、 註冊和取消註冊物件的相關資訊。  
  
 **CreatorMap**包含下列資訊：  
  
-   如何初始化、 註冊和取消註冊的物件。  
  
-   比較傳統的 COM 或 Windows 執行階段 factory 根據啟用資料的方式。  
  
-   介面的處理站快取和伺服器名稱的相關資訊。  
  
## <a name="members"></a>成員  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CreatorMap::activationId 資料成員](../windows/creatormap-activationid-data-member.md)|表示透過傳統的 COM 類別識別碼或 Windows 執行階段名稱識別的物件識別碼。|  
|[CreatorMap::factoryCache 資料成員](../windows/creatormap-factorycache-data-member.md)|儲存的處理站快取指標**CreatorMap**。|  
|[CreatorMap::factoryCreator 資料成員](../windows/creatormap-factorycreator-data-member.md)|建立指定的 factory **CreatorMap**。|  
|[CreatorMap::serverName 資料成員](../windows/creatormap-servername-data-member.md)|儲存的伺服器名稱**CreatorMap**。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CreatorMap`  
  
## <a name="requirements"></a>需求  
 **標頭：** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)