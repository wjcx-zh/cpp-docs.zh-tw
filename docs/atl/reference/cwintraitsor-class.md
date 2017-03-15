---
title: "CWinTraitsOR 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CWinTraitsOR
- ATL::CWinTraitsOR
- CWinTraitsOR
dev_langs:
- C++
helpviewer_keywords:
- CWinTraitsOR class
- window styles, default values for ATL
ms.assetid: 1eb7b1e8-a9bd-411b-a30a-35a8a10af989
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cd077c7f79c3099d0e825a48233e7a8b269c0d04
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraitsor-class"></a>CWinTraitsOR 類別
這個類別提供建立視窗物件時所使用之樣式標準化的方法。  
  
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
 預設延伸的視窗樣式。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinTraitsOR::GetWndExStyle](#getwndexstyle)|擷取的延伸的樣式`CWinTraitsOR`物件。|  
|[CWinTraitsOR::GetWndStyle](#getwndstyle)|擷取標準樣式`CWinTraitsOR`物件。|  
  
## <a name="remarks"></a>備註  
 這[視窗特性](../../atl/understanding-window-traits.md)類別會提供簡單的方法標準化用於建立 ATL 視窗物件的樣式。 使用此類別的特製化，做為範本參數[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或 ATL 的視窗類別，來指定要用於標準與擴充樣式的最小集合的另一個視窗類別的執行個體。  
  
 如果您想要確定特定樣式設定為視窗類別的所有執行個體同時允許其他樣式設定每個執行個體為基礎的呼叫中使用此範本的特製化[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 如果您想要提供預設的樣式，將在沒有其他樣式會指定在呼叫時，才使用`CWindowImpl::Create`，使用[CWinTraits](../../atl/reference/cwintraits-class.md)改。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-namegetwndstylea--cwintraitsorgetwndstyle"></a><a name="getwndstyle"></a>CWinTraitsOR::GetWndStyle  
 呼叫此函式可擷取組合 （使用邏輯 OR 運算子） 的標準樣式`CWinTraits`物件和所指定的預設樣式`t_dwStyle`。  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 用來建立視窗的樣式。  
  
### <a name="return-value"></a>傳回值  
 傳入的樣式的組合`dwStyle`和預設值是由`t_dwStyle`，使用邏輯 OR 運算子。  
  
##  <a name="a-namegetwndexstylea--cwintraitsorgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraitsOR::GetWndExStyle  
 呼叫此函式可擷取組合 （使用邏輯 OR 運算子） 的延伸樣式`CWinTraits`物件和所指定的預設樣式`t_dwStyle`。  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 用來建立視窗的延伸的樣式。  
  
### <a name="return-value"></a>傳回值  
 傳入的延伸樣式的組合`dwExStyle`及所指定的預設`t_dwExStyle`，使用邏輯 OR 運算子  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [了解視窗特性](../../atl/understanding-window-traits.md)


