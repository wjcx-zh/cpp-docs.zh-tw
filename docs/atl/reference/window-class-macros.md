---
title: 視窗類別巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
dev_langs:
- C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 470c1c8e3facbeba909e182b97a8b027dc9e8ca8
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879677"
---
# <a name="window-class-macros"></a>視窗類別巨集
這些巨集會定義視窗類別的公用程式。  
  
|||  
|-|-|  
|[{2&AMP;GT;DECLARE_WND_CLASS&AMP;LT;2](#declare_wnd_class)|可讓您指定新的視窗類別名稱。| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017)可讓您指定新的視窗類別，並在封入類別的新類別會使用其視窗程序的名稱。| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|可讓您指定的現有視窗類別為基礎的新的視窗類別名稱。|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|可讓您指定類別的參數。|  

## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
   
##  <a name="declare_wnd_class"></a>  {2&AMP;GT;DECLARE_WND_CLASS&AMP;LT;2  
 可讓您指定新的視窗類別名稱。 將這個巨集放在 ATL ActiveX 控制項的控制項類別。  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>參數  
 *WndClassName*  
 [in]新的視窗類別名稱。 如果是 NULL，ATL 會產生視窗類別名稱。  
  
### <a name="remarks"></a>備註  
 如果您使用 /permissive-compiler 選項，然後 {2&gt;declare_wnd_class&lt;2 會造成編譯器錯誤;請改用 DECLARE_WND_CLASS2。
 
 {2&gt;declare_wnd_class&lt;2 可讓您指定新的視窗類別，將由管理其資訊的名稱[CWndClassInfo](cwndclassinfo-class.md)。 {2&gt;declare_wnd_class&lt;2 會定義新的視窗類別，藉由實作下列靜態函式：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 {2&gt;declare_wnd_class&lt;2 指定新的視窗中的下列樣式：  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 {2&gt;declare_wnd_class&lt;2 也會指定預設的視窗背景色彩。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)巨集來提供您自己的樣式和背景色彩。  
  
 [CWindowImpl](cwindowimpl-class.md)使用 {2&gt;declare_wnd_class&lt;2 巨集來建立新的視窗類別為基礎的視窗。 若要覆寫此行為，請使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)巨集，或提供您自己實作[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函式。  

  
 如需有關如何使用 ATL 中的 windows 的詳細資訊，請參閱[ATL 視窗類別](../../atl/atl-window-classes.md)。  

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2  
 (Visual Studio 2017)類似 {2&gt;declare_wnd_class&lt;2，但具有額外的參數使用 /permissive-option 進行編譯時，避免相依名稱時發生錯誤。
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>參數  
 *WndClassName*  
 [in]新的視窗類別名稱。 如果是 NULL，ATL 會產生視窗類別名稱。 

 *EnclosingClass*  
 [in]包含新的視窗類別的視窗類別名稱。 不可以是 NULL。  
  
### <a name="remarks"></a>備註 
如果您使用 /permissive-option，然後 {2&gt;declare_wnd_class&lt;2 會造成編譯錯誤因為它包含相依的名稱。 DECLARE_WND_CLASS2 需要您明確命名的類別，這個巨集使用中，而且不會下 /permissive-flag 錯誤。
否則，這個巨集就等於[{2&gt;declare_wnd_class&lt;2](#declare_wnd_class)。
   
##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS  
 可讓您指定類別的參數。 將這個巨集放在 ATL ActiveX 控制項的控制項類別。  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>參數  
 *WndClassName*  
 [in]視窗名稱類別，將超級類別*OrigWndClassName*。 如果是 NULL，ATL 會產生視窗類別名稱。  
  
 *OrigWndClassName*  
 [in]現有視窗類別名稱。  
  
### <a name="remarks"></a>備註  
 這個巨集可讓您指定的視窗類別，將超級類別現有視窗類別名稱。 [CWndClassInfo](cwndclassinfo-class.md)管理超級類別的資訊。  
  
 DECLARE_WND_SUPERCLASS 會實作下列靜態函式：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 根據預設， [CWindowImpl](cwindowimpl-class.md)會使用[{2&gt;declare_wnd_class&lt;2](#declare_wnd_class)巨集來建立視窗會根據新的視窗類別。 藉由指定 DECLARE_WND_SUPERCLASS 巨集，在`CWindowImpl`-衍生的類別，視窗類別會根據現有類別，但會使用您的視窗程序。 這項技術稱為 superclassing。  
  
 除了使用 {2&gt;declare_wnd_class&lt;2 和 DECLARE_WND_SUPERCLASS 巨集，您可以覆寫[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函式，使用您自己的實作。  

  
 如需有關如何使用 ATL 中的 windows 的詳細資訊，請參閱[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX  
 可讓您指定的現有視窗類別為基礎的新的視窗類別名稱。 將這個巨集放在 ATL ActiveX 控制項的控制項類別。  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>參數  
 *WndClassName*  
 [in]新的視窗類別名稱。 如果是 NULL，ATL 會產生視窗類別名稱。  
  
 *style*  
 [in]視窗的樣式。  
  
 *背景*  
 [in]視窗的背景色彩。  
  
### <a name="remarks"></a>備註  
 這個巨集可讓您指定新的視窗類別，將由管理其資訊的類別參數[CWndClassInfo](cwndclassinfo-class.md)。 DECLARE_WND_CLASS_EX 定義新的視窗類別，藉由實作下列靜態函式：  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 如果您想要使用的預設樣式和背景色彩，使用[{2&gt;declare_wnd_class&lt;2](#declare_wnd_class)巨集。 如需有關如何使用 ATL 中的 windows 的詳細資訊，請參閱[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](atl-macros.md)









