---
title: "CWinTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- CMDIChildWinTraits
- ATL.CWinTraits
- CFrameWinTraits
- ATL::CWinTraits
- CControlWinTraits
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: abd62b916f976721bf85fc4bb2a94ffaf5b217ea
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraits-class"></a>CWinTraits 類別
這個類別提供建立視窗物件時所使用之樣式標準化的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>參數  
 `t_dwStyle`  
 預設標準的視窗樣式。  
  
 `t_dwExStyle`  
 預設延伸的視窗樣式。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|（靜態）擷取的延伸的樣式`CWinTraits`物件。|  
|[CWinTraits::GetWndStyle](#getwndstyle)|（靜態）擷取標準樣式`CWinTraits`物件。|  
  
## <a name="remarks"></a>備註  
 這[視窗特性](../../atl/understanding-window-traits.md)類別會提供簡單的方法標準化用於建立 ATL 視窗物件的樣式。 使用此類別的特製化，做為範本參數[CWindowImpl](../../atl/reference/cwindowimpl-class.md)或另一個 ATL 的視窗類別，來指定所使用的預設標準與擴充樣式的視窗類別的執行個體。  
  
 使用此範本，當您想要提供預設的呼叫中不指定任何其他樣式時，才會使用的視窗樣式[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)。  
  
 ATL 提供三個預先定義的特製化的視窗樣式的常用組合此範本︰  
  
 `CControlWinTraits`  
 標準控制項視窗的設計。 使用下列標準的樣式︰ **WS_CHILD**， **WS_VISIBLE**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 沒有延伸的樣式。  
  
 `CFrameWinTraits`  
 設計標準的框架視窗。 使用標準樣式包括︰ **WS_OVERLAPPEDWINDOW**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 使用延伸的樣式包括︰ **WS_EX_APPWINDOW**和**WS_EX_WINDOWEDGE**。  
  
 `CMDIChildWinTraits`  
 設計標準的 MDI 子視窗。 使用標準樣式包括︰ **WS_OVERLAPPEDWINDOW**， **WS_CHILD**， **WS_VISIBLE**， **WS_CLIPCHILDREN**，和**WS_CLIPSIBLINGS**。 使用延伸的樣式包括︰ **WS_EX_MDICHILD**。  
  
 如果您想要確保特定樣式所設定的所有執行個體同時允許設定個別執行個體為基礎的其他樣式的視窗類別的使用[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)改。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-namegetwndstylea--cwintraitsgetwndstyle"></a><a name="getwndstyle"></a>CWinTraits::GetWndStyle  
 呼叫此函式可擷取的標準樣式`CWinTraits`物件。  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 標準的樣式，用於建立視窗。 如果`dwStyle`為 0，範本的樣式值 ( `t_dwStyle`) 會傳回。 如果`dwStyle`是零，`dwStyle`會傳回。  
  
### <a name="return-value"></a>傳回值  
 物件的標準的視窗樣式。  
  
##  <a name="a-namegetwndexstylea--cwintraitsgetwndexstyle"></a><a name="getwndexstyle"></a>CWinTraits::GetWndExStyle  
 呼叫此函式可擷取的延伸的樣式`CWinTraits`物件。  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 用來建立視窗的延伸的樣式。 如果`dwExStyle`為 0，範本的樣式值 ( `t_dwExStyle`) 會傳回。 如果`dwExStyle`是零，`dwExStyle`會傳回。  
  
### <a name="return-value"></a>傳回值  
 物件的延伸的視窗樣式。  
  
## <a name="see-also"></a>另請參閱  
 [類別成員](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [類別概觀](../../atl/atl-class-overview.md)   
 [了解視窗特性](../../atl/understanding-window-traits.md)

