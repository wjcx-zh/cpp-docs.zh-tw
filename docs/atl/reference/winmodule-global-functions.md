---
title: "WinModule 全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: c477f4500bd4fe78f21f04c58b02d1b493f72c01
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="winmodule-global-functions"></a>WinModule 全域函式
這些函式提供的支援`_AtlCreateWndData`結構的作業。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|此函式是用來初始化及加入 `_AtlCreateWndData` 結構。|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
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
 模組指標[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構。  
  
 `pData`  
 指標[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構，以初始化，並加入至目前的模組。  
  
 `pObject`  
 物件的指標**這**指標。  
  
### <a name="remarks"></a>備註  
 初始化`_AtlCreateWndData`結構，用來儲存**這**指標用來參考類別執行個體，並將它加入至清單的模組參考之`_ATL_WIN_MODULE70`結構。 由呼叫[CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata)。  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 呼叫此函式可擷取現有的 `_AtlCreateWndData` 結構。  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>參數  
 `pWinModule`  
 模組指標[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)結構。  
  
### <a name="return-value"></a>傳回值  
 傳回的指標[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構。  
  
### <a name="remarks"></a>備註  
 此函式會擷取現有`_AtlCreateWndData`從清單中的模組所參考的結構`_ATL_WIN_MODULE70`結構。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

