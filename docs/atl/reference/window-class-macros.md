---
title: "視窗類別巨集 |Microsoft 文件"
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
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
caps.latest.revision: 16
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
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: f32926b6efd4ffb9c0541c0574a479c13dac01df
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="window-class-macros"></a>視窗類別巨集
這些巨集定義 視窗類別的公用程式。  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|可讓您指定新的視窗類別名稱。| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017)可讓您指定新的視窗類別，與封入類別的新類別會使用其視窗程序的名稱。| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|可讓您指定新的視窗類別依據現有視窗類別名稱。|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|可讓您指定類別的參數。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
   
##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS  
 可讓您指定新的視窗類別名稱。 將這個巨集放在 ATL ActiveX 控制項的控制項類別。  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>參數  
 `WndClassName`  
 [in]新的視窗類別名稱。 如果**NULL**，ATL 產生的視窗類別名稱。  
  
### <a name="remarks"></a>備註  
 如果您使用 /permissive-compiler 選項，然後 DECLARE_WND_CLASS 會造成編譯器錯誤。請改用 DECLARE_WND_CLASS2。
 
 DECLARE_WND_CLASS 可讓您指定其資訊就會受到新的視窗類別名稱[CWndClassInfo](cwndclassinfo-class.md)。 `DECLARE_WND_CLASS`藉由實作下列靜態函式定義新的視窗類別︰  
  
 [!code-cpp[NVC_ATL_Windowing #&127;](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS`指定新視窗中的下列樣式︰  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS`也會指定預設視窗的背景色彩。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)巨集，以提供您自己的樣式和背景色彩。  
  
 [CWindowImpl](cwindowimpl-class.md)使用`DECLARE_WND_CLASS`巨集來建立視窗是根據新的視窗類別。 若要覆寫這個行為，請使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)巨集，或提供您自己實作[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函式。  

  
 如需在 ATL 中使用 windows 的詳細資訊，請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。  

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2  
 (Visual Studio 2017)類似於 DECLARE_WND_CLASS，具有額外的參數，使用 /permissive-option 編譯時，避免因為相依名稱錯誤。
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>參數  
 `WndClassName`  
 [in]新的視窗類別名稱。 如果**NULL**，ATL 產生的視窗類別名稱。 

 `EnclosingClass`  
 [in]封入新的視窗類別之視窗類別的名稱。 不能是**NULL**。  
  
### <a name="remarks"></a>備註 
如果您使用 /permissive-option，然後 DECLARE_WND_CLASS 會造成編譯錯誤因為有相依的名稱。 DECLARE_WND_CLASS2 會要求您明確地將這個巨集使用中，而且不會在 /permissive-flag 錯誤類別。
否則這個巨集等同於[DECLARE_WND_CLASS](#declare_wnd_class)。
   
##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS  
 可讓您指定類別的參數。 將這個巨集放在 ATL ActiveX 控制項的控制項類別。  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>參數  
 `WndClassName`  
 [in]視窗名稱的類別，將超級類別`OrigWndClassName`。 如果**NULL**，ATL 產生的視窗類別名稱。  
  
 `OrigWndClassName`  
 [in]現有視窗類別名稱。  
  
### <a name="remarks"></a>備註  
 這個巨集可讓您指定的視窗類別，將現有視窗類別的超級類別名稱。 [CWndClassInfo](cwndclassinfo-class.md)管理的超級類別資訊。  
  
 `DECLARE_WND_SUPERCLASS`會實作下列靜態函式︰  
  
 [!code-cpp[NVC_ATL_Windowing #&127;](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 根據預設， [CWindowImpl](cwindowimpl-class.md)使用[DECLARE_WND_CLASS](#declare_wnd_class)巨集來建立視窗是根據新的視窗類別。 藉由指定`DECLARE_WND_SUPERCLASS`中的巨集`CWindowImpl`-衍生類別中，視窗類別會根據現有的類別，但將使用您的視窗程序。 這項技術稱為 superclassing。  
  
 除了使用`DECLARE_WND_CLASS`和`DECLARE_WND_SUPERCLASS`巨集，可以覆寫[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函式，以您自己的實作。  

  
 如需在 ATL 中使用 windows 的詳細資訊，請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX  
 可讓您指定新的視窗類別依據現有視窗類別名稱。 將這個巨集放在 ATL ActiveX 控制項的控制項類別。  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>參數  
 `WndClassName`  
 [in]新的視窗類別名稱。 如果**NULL**，ATL 產生的視窗類別名稱。  
  
 `style`  
 [in]視窗樣式。  
  
 *背景*  
 [in]視窗的背景色彩。  
  
### <a name="remarks"></a>備註  
 這個巨集可讓您指定新的視窗類別，將受其資訊的類別參數[CWndClassInfo](cwndclassinfo-class.md)。 `DECLARE_WND_CLASS_EX`藉由實作下列靜態函式定義新的視窗類別︰  
  
 [!code-cpp[NVC_ATL_Windowing #&127;](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 如果您想要使用的預設樣式和背景色彩，請使用[DECLARE_WND_CLASS](#declare_wnd_class)巨集。 如需在 ATL 中使用 windows 的詳細資訊，請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](atl-macros.md)










