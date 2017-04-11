---
title: "CAtlWinModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: f2d5e28f39159b097c4e00e11518295b2872a84b
ms.lasthandoff: 03/31/2017

---
# <a name="catlwinmodule-class"></a>CAtlWinModule 類別
這個類別提供 ATL 視窗化元件的支援。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlWinModule : public _ATL_WIN_MODULE
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|建構函式。|  
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|加入資料物件。|  
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|傳回視窗模組資料物件的指標。|  
  
## <a name="remarks"></a>備註  
 這個類別會提供所有的 ATL 類別需要視窗化功能的支援。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)  
  
 `CAtlWinModule`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
##  <a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData  
 這個方法會初始化並新增`_AtlCreateWndData`結構。  
  
```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```  
  
### <a name="parameters"></a>參數  
 `pData`  
 指標`_AtlCreateWndData`結構來初始化及加入至目前的模組。  
  
 `pObject`  
 物件的指標**這**指標。  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫[AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata)哪些初始化[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)結構。 此結構會儲存**這**指標，用來取得視窗程序中的類別執行個體。  
  
##  <a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule  
 建構函式。  
  
```
CAtlWinModule();
```  
  
### <a name="remarks"></a>備註  
 如果初始化失敗， **EXCEPTION_NONCONTINUABLE**引發例外狀況。  
  
##  <a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule  
 解構函式。  
  
```
~CAtlWinModule();
```  
  
### <a name="remarks"></a>備註  
 釋放所有配置的資源。  
  
##  <a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData  
 這個方法會傳回指標`_AtlCreateWndData`結構。  
  
```
void* ExtractCreateWndData();
```  
  
### <a name="return-value"></a>傳回值  
 將指標傳回至`_AtlCreateWndData`先前加入的結構[CAtlWinModule::AddCreateWndData](#addcreatewnddata)，或如果沒有物件可供使用，則為 NULL。  
  
## <a name="see-also"></a>另請參閱  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)

