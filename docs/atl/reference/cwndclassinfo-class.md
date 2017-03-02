---
title: "CWndClassInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWndClassInfo
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: 22
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: f036d79c7a9420e083eb86023c5cbf98906cc1cc
ms.lasthandoff: 02/24/2017

---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 類別
這個類別提供方法來登錄視窗類別資訊。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CWndClassInfo
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|[註冊](#register)|註冊視窗類別。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_atom](#m_atom)|可唯一識別已註冊的視窗類別。|  
|[m_bSystemCursor](#m_bsystemcursor)|指定的游標資源參考系統游標或在模組資源中所包含的資料指標。|  
|[m_lpszCursorID](#m_lpszcursorid)|指定的游標資源名稱。|  
|[m_lpszOrigName](#m_lpszorigname)|包含現有視窗類別名稱。|  
|[m_szAutoName](#m_szautoname)|保留產生的 ATL 視窗類別的名稱。|  
|[m_wc](#m_wc)|維護中的視窗類別資訊**WNDCLASSEX**結構。|  
|[pWndProc](#pwndproc)|指向視窗程序的現有視窗類別。|  
  
## <a name="remarks"></a>備註  
 `CWndClassInfo`管理視窗類別的資訊。 您通常會使用`CWndClassInfo`透過三個巨集，其中`DECLARE_WND_CLASS`， `DECLARE_WND_CLASS_EX`，或`DECLARE_WND_SUPERCLASS`下, 表所述︰  
  
|巨集|描述|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)|`CWndClassInfo`為新的視窗類別登錄資訊。|  
|[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)|`CWndClassInfo`登錄新的視窗類別，其中包括類別參數的資訊。|  
|[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)|`CWndClassInfo`註冊視窗類別，根據現有的類別，但使用不同的視窗程序的資訊。 這項技術稱為 superclassing。|  
  
 根據預設， [CWindowImpl](../../atl/reference/cwindowimpl-class.md)包含`DECLARE_WND_CLASS`巨集來建立視窗是根據新的視窗類別。 DECLARE_WND_CLASS 提供控制項的預設樣式和背景色彩。 如果您想要指定樣式和背景色彩自己，衍生您的類別，從`CWindowImpl`，並包含`DECLARE_WND_CLASS_EX`在類別定義中的巨集。  
  
 如果您想要建立視窗，根據現有的視窗類別，衍生您的類別，從`CWindowImpl`，並包含`DECLARE_WND_SUPERCLASS`在類別定義中的巨集。 例如：  
  
 [!code-cpp[NVC_ATL_Windowing #&43;](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 如需視窗類別的詳細資訊，請參閱[視窗類別](http://msdn.microsoft.com/library/windows/desktop/ms632596)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需在 ATL 中使用 windows 的詳細資訊，請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="a-namematoma--cwndclassinfomatom"></a><a name="m_atom"></a>CWndClassInfo::m_atom  
 包含已註冊的視窗類別的唯一識別碼。  
  
```
ATOM m_atom;
```  
  
##  <a name="a-namembsystemcursora--cwndclassinfombsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor  
 如果**TRUE**，註冊視窗類別時，將其載入系統游標資源。  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>備註  
 否則，會載入包含在模組中的游標資源。  
  
 `CWndClassInfo`使用`m_bSystemCursor`時，才[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (預設值在[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)指定巨集。 在此情況下，`m_bSystemCursor`會初始化為**TRUE**。 如需詳細資訊，請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="a-namemlpszcursorida--cwndclassinfomlpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID  
 低序位字組和零高序位文字中的指定的游標資源的名稱或資源識別碼。  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>備註  
 註冊視窗類別時，資料指標所識別的控制代碼`m_lpszCursorID`擷取和儲存[m_wc](#m_wc)。  
  
 `CWndClassInfo`使用`m_lpszCursorID`時，才[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (預設值在[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)指定巨集。 在此情況下，`m_lpszCursorID`會初始化為**IDC_ARROW**。 如需詳細資訊，請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="a-namemlpszorignamea--cwndclassinfomlpszorigname"></a><a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName  
 包含現有視窗類別名稱。  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>備註  
 `CWndClassInfo`使用`m_lpszOrigName`只有當您加入[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)在類別定義中的巨集。 在此情況下，`CWndClassInfo`暫存器視窗類別根據由名為的類別`m_lpszOrigName`。 如需詳細資訊，請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="a-namemszautonamea--cwndclassinfomszautoname"></a><a name="m_szautoname"></a>CWndClassInfo::m_szAutoName  
 保留視窗類別的名稱。  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>備註  
 `CWndClassInfo`使用`m_szAutoName`才**NULL**傳遞給`WndClassName`參數[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971)、 [DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)或[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)。 註冊視窗類別時，ATL 會建構一個名稱。  
  
##  <a name="a-namemwca--cwndclassinfomwc"></a><a name="m_wc"></a>CWndClassInfo::m_wc  
 維護中的視窗類別資訊[WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577)結構。  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>備註  
 如果您已指定[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (預設值在[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)巨集，`m_wc`包含新的視窗類別的相關資訊。  
  
 如果您已指定[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)巨集，`m_wc`包含超級類別資訊 — 視窗類別，根據現有的類別，但使用不同的視窗程序。 [m_lpszOrigName](#m_lpszorigname)和[pWndProc](#pwndproc)分別儲存現有的視窗類別名稱和視窗程序。  
  
##  <a name="a-namepwndproca--cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc  
 指向視窗程序的現有視窗類別。  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>備註  
 `CWndClassInfo`使用`pWndProc`只有當您加入[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)在類別定義中的巨集。 在此情況下，`CWndClassInfo`註冊視窗類別，根據現有的類別，但使用不同的視窗程序。 現有視窗類別的視窗程序儲存在`pWndProc`。 如需詳細資訊，請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="a-nameregistera--cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::Register  
 由呼叫[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)註冊視窗類別，如果尚未註冊。  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>參數  
 `pProc`  
 [out]指定現有視窗類別的原始視窗程序。  
  
### <a name="return-value"></a>傳回值  
 如果成功，atom 可唯一識別所註冊視窗類別。 否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您已指定[DECLARE_WND_CLASS](http://msdn.microsoft.com/library/55247a72-fb9e-4bde-87f3-747c08076971) (預設值在[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](http://msdn.microsoft.com/library/0672c144-f2aa-4f6a-ae16-566e3a1f5411)巨集，`Register`會註冊新的視窗類別。 在此情況下，`pProc`不使用參數。  
  
 如果您已指定[DECLARE_WND_SUPERCLASS](http://msdn.microsoft.com/library/650337b6-4973-41e5-8c36-55f90327bdcd)巨集，`Register`註冊超級類別 — 視窗類別，根據現有的類別，但使用不同的視窗程序。 現有視窗類別的視窗程序中，會傳回`pProc`。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
