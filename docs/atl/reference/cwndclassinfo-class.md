---
title: CWndClassInfo 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
dev_langs:
- C++
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b328cb869f971afb0251750d7847d6850688731
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879831"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 類別
這個類別提供方法來註冊視窗類別資訊。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CWndClassInfo
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|[註冊](#register)|註冊視窗類別。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_atom](#m_atom)|可唯一識別已註冊的視窗類別。|  
|[m_bSystemCursor](#m_bsystemcursor)|指定的游標資源是否參考系統資料指標，或模組資源中包含的資料指標。|  
|[m_lpszCursorID](#m_lpszcursorid)|指定游標資源的名稱。|  
|[m_lpszOrigName](#m_lpszorigname)|包含現有視窗類別名稱。|  
|[m_szAutoName](#m_szautoname)|保留 ATL 產生的視窗類別名稱。|  
|[m_wc](#m_wc)|維護中的視窗類別資訊`WNDCLASSEX`結構。|  
|[pWndProc](#pwndproc)|指向視窗程序的現有視窗類別。|  
  
## <a name="remarks"></a>備註  
 `CWndClassInfo` 管理視窗類別的資訊。 您通常會使用`CWndClassInfo`透過三個巨集、 {2&gt;declare_wnd_class&lt;2、 DECLARE_WND_CLASS_EX，還是 DECLARE_WND_SUPERCLASS 下, 表中所述的其中一個：  
  
|巨集|描述|  
|-----------|-----------------|  
|[{2&AMP;GT;DECLARE_WND_CLASS&AMP;LT;2](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` 註冊新的視窗類別的資訊。|  
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` 註冊新的視窗類別，其中包括類別參數的資訊。|  
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` 註冊視窗類別以現有的類別為基礎，但使用不同的視窗程序的資訊。 這項技術稱為 superclassing。|  
  
 根據預設， [CWindowImpl](../../atl/reference/cwindowimpl-class.md)包含`DECLARE_WND_CLASS`巨集來建立視窗會根據新的視窗類別。 {2&gt;declare_wnd_class&lt;2 提供控制項的預設樣式和背景色彩。 如果您想要指定樣式和您自己的背景色彩，衍生您的類別，從`CWindowImpl`並將您的類別定義中納入 DECLARE_WND_CLASS_EX 巨集。  
  
 如果您想要建立視窗，根據現有的視窗類別，衍生您的類別，從`CWindowImpl`並將您的類別定義中納入 DECLARE_WND_SUPERCLASS 巨集。 例如:   
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 如需視窗類別的詳細資訊，請參閱[視窗類別](http://msdn.microsoft.com/library/windows/desktop/ms632596)Windows SDK 中。  
  
 如需有關如何使用 ATL 中的 windows 的詳細資訊，請參閱[ATL 視窗類別](../../atl/atl-window-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="m_atom"></a>  CWndClassInfo::m_atom  
 包含已註冊的視窗類別的唯一識別碼。  
  
```
ATOM m_atom;
```  
  
##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor  
 如果為 TRUE，註冊視窗類別時，將會載入系統游標資源。  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>備註  
 否則，會載入包含在模組中的游標資源。  
  
 `CWndClassInfo` 會使用`m_bSystemCursor`時，才[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (在預設[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)指定巨集。 在此情況下，`m_bSystemCursor`會初始化為 TRUE。 如需詳細資訊，請參閱 < [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID  
 低序位字組和零的高序位文字中指定的游標資源的名稱或資源識別碼。  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>備註  
 註冊視窗類別時，資料指標所識別的控制代碼`m_lpszCursorID`擷取和儲存[m_wc](#m_wc)。  
  
 `CWndClassInfo` 會使用`m_lpszCursorID`時，才[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (在預設[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)指定巨集。 在此情況下，`m_lpszCursorID`會初始化為 IDC_ARROW。 如需詳細資訊，請參閱 < [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName  
 包含現有視窗類別名稱。  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>備註  
 `CWndClassInfo` 會使用`m_lpszOrigName`只有當您加入[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)類別定義中的巨集。 在此情況下，`CWndClassInfo`所命名的類別為基礎的視窗類別註冊`m_lpszOrigName`。 如需詳細資訊，請參閱 < [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName  
 保留視窗類別名稱。  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>備註  
 `CWndClassInfo` 會使用`m_szAutoName`只有 NULL 會傳遞給`WndClassName`參數來[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class)，則[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)或是[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL 視窗類別註冊時，會建構名稱。  
  
##  <a name="m_wc"></a>  CWndClassInfo::m_wc  
 維護中的視窗類別資訊[WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577)結構。  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>備註  
 如果您已指定[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (在預設[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)巨集，`m_wc`包含的相關資訊新的視窗類別。  
  
 如果您已指定[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集，`m_wc`包含超級類別資訊 — 以現有的類別為基礎，但使用不同的視窗程序的視窗類別。 [m_lpszOrigName](#m_lpszorigname)並[pWndProc](#pwndproc)分別儲存現有的視窗類別名稱和視窗程序。  
  
##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc  
 指向視窗程序的現有視窗類別。  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>備註  
 `CWndClassInfo` 會使用`pWndProc`只有當您加入[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)類別定義中的巨集。 在此情況下，`CWndClassInfo`註冊視窗類別以現有的類別為基礎，但使用不同的視窗程序。 現有視窗類別的視窗程序會儲存在`pWndProc`。 如需詳細資訊，請參閱 < [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概觀。  
  
##  <a name="register"></a>  CWndClassInfo::Register  
 由呼叫[CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create)註冊視窗類別，如果尚未註冊。  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>參數  
 *pProc*  
 [out]指定現有視窗類別的原始視窗程序。  
  
### <a name="return-value"></a>傳回值  
 如果成功，atom 可唯一識別所註冊的 window 類別。 否則就是 0。  
  
### <a name="remarks"></a>備註  
 如果您已指定[{2&gt;declare_wnd_class&lt;2](window-class-macros.md#declare_wnd_class) (在預設[CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)巨集，`Register`註冊新的視窗類別。 在此情況下， *pProc*不使用參數。  
  
 如果您已指定[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)巨集，`Register`註冊超級類別，以現有的類別為基礎，但使用不同的視窗程序的視窗類別。 現有視窗類別的視窗程序都會傳入*pProc*。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)