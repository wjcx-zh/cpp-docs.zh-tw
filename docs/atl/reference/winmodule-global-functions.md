---
title: "全域函式 WinModule |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs: C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 290566c27fa5698c4a00a323a8c2431681b69d88
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="winmodule-global-functions"></a>WinModule 全域函式
這些函式提供的支援`_AtlCreateWndData`結構的作業。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函式是用來初始化及加入 `_AtlCreateWndData` 結構。|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。|  

## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData  
 此函式是用來初始化及加入 `_AtlCreateWndData` 結構。  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>參數  
 `pWinModule`  
 模組的指標[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構。  
  
 `pData`  
 指標[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構來初始化及加入至目前的模組。  
  
 `pObject`  
 物件的指標**這**指標。  
  
### <a name="remarks"></a>備註  
 初始化`_AtlCreateWndData`結構，也就用來儲存**這**指標用來參考類別執行個體，並將它加入至清單的模組參考之`_ATL_WIN_MODULE70`結構。 由呼叫[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)。  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>參數  
 `pWinModule`  
 模組的指標[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構。  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 此函式會擷取現有`_AtlCreateWndData`從清單中的模組所參考的結構`_ATL_WIN_MODULE70`結構。  
  
## <a name="see-also"></a>請參閱  
 [函式](../../atl/reference/atl-functions.md)
