---
title: "CWinTraitsOR 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR
- ATLWIN/ATL::CWinTraitsOR::GetWndExStyle
- ATLWIN/ATL::CWinTraitsOR::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac6cf07fcd6d3703ffb6b483ba19a2d12520cb0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 類別
這個類別會提供建立視窗物件時所使用之樣式標準化的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <DWORD t_dwStyle = 0,
          DWORD t_dwExStyle = 0, 
          class TWinTraits = CControlWinTraits>
class CWinTraitsOR
```  
  
#### <a name="parameters"></a>參數  
 `t_dwStyle`  
 預設視窗樣式。  
  
 `t_dwExStyle`  
 預設的延伸的視窗樣式。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|擷取的延伸的樣式`CWinTraitsOR`物件。|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|擷取標準樣式`CWinTraitsOR`物件。|  
  
## <a name="remarks"></a>備註  
 這[視窗特性](../../atl/understanding-window-traits.md)類別會提供用於建立 ATL 視窗物件之樣式標準化的簡單方法。 為範本參數，以使用這個類別的特製化[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或 ATL 的視窗類別，來指定要用於標準與擴充樣式的最小集合的另一個視窗類別的執行個體。  
  
 如果您想要確定特定樣式設定視窗類別的所有執行個體同時允許其他樣式設定針對每個執行個體的呼叫中使用此範本的特製化[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 如果您想要提供預設的呼叫中不指定任何其他樣式時，才會使用的視窗樣式`CWindowImpl::Create`，使用[CWinTraits](../../atl/reference/cwintraits-class.md)改為。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 呼叫此函式可擷取 （使用邏輯 OR 運算子） 的標準的樣式組合`CWinTraits`物件和所指定的預設樣式`t_dwStyle`。  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 用來建立視窗的樣式。  
  
### <a name="return-value"></a>傳回值  
 傳入的樣式的組合`dwStyle`和預設值是由`t_dwStyle`，使用邏輯 OR 運算子。  
  
##  <a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 呼叫此函式可擷取 （使用邏輯 OR 運算子） 的擴充樣式的組合`CWinTraits`物件和所指定的預設樣式`t_dwStyle`。  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 用來建立視窗的延伸的樣式。  
  
### <a name="return-value"></a>傳回值  
 傳入的延伸樣式的組合`dwExStyle`及所指定的預設`t_dwExStyle`，使用邏輯 OR 運算子  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [了解視窗特性](../../atl/understanding-window-traits.md)

