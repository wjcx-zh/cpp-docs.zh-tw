---
title: CReBar 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ea2a1047864c19be3f5bbd6c303b4b00fb132dc
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078763"
---
# <a name="crebar-class"></a>CReBar 類別
提供 Rebar 控制項配置、持續性和狀態資訊的控制列。  
  
## <a name="syntax"></a>語法  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|將 rebar 群組列。|  
|[CReBar::Create](#create)|建立 rebar 控制項，並將它附加至`CReBar`物件。|  
|[Crebar:: Getrebarctrl](#getrebarctrl)|允許直接存取基礎的通用控制項。|  
  
## <a name="remarks"></a>備註  
 Rebar 物件可以包含各種子視窗 (通常是其他控制項)，包括編輯方塊、工具列和清單方塊。 Rebar 物件可以在指定的點陣圖上顯示其子視窗。 您的應用程式可以自動調整 rebar，或使用者可以透過按一下或拖曳它的移駐夾列手動調整 rebar。  
  
 ![Rebarmenu 範例](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Rebar 控制項  
 Rebar 物件的行為類似工具列物件。 Rebar 使用按一下並拖曳機制來調整其群組列的大小。 Rebar 控制項可以包含一個或多個群組列，而且每個群組列都具有移駐夾列、點陣圖、文字標籤和子視窗中的任何組合。 不過，群組列不能包含一個以上的子視窗。  
  
 `CReBar` 使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)類別，以提供它的實作。 您可以存取透過 rebar 控制項[GetReBarCtrl](#getrebarctrl)利用控制項的自訂選項。 如需 rebar 控制項的詳細資訊，請參閱`CReBarCtrl`。 如需使用 rebar 控制項的詳細資訊，請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
> [!CAUTION]
>  Rebar 和 rebar 控制項物件不支援 MFC 控制列的停駐。 如果`CRebar::EnableDocking`呼叫時，您的應用程式會判斷提示。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
##  <a name="addbar"></a>  CReBar::AddBar  
 呼叫此成員函式加入 rebar 群組列。  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

 
BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>參數  
 *pBar*  
 指標`CWnd`是要插入至 rebar 的子視窗的物件。 參考的物件必須具有**WS_CHILD**。  
  
 *lpszText*  
 字串，包含 rebar 上顯示的文字指標。 **NULL**預設。 中包含的文字*lpszText*不屬於子視窗，其位於 rebar 本身。  
  
 *pbmp*  
 指標`CBitmap`rebar 背景上顯示的物件。 **NULL**預設。  
  
 *dwStyle*  
 A`DWORD`包含要套用至 rebar 的樣式。 請參閱**fStyle**函數中的 Win32 結構描述[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)如需完整的頻外樣式清單。  
  
 *clrFore*  
 A **COLORREF**值，表示 rebar 的前景色彩。  
  
 *clrBack*  
 A **COLORREF**值，表示 rebar 的背景色彩。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>  CReBar::Create  
 呼叫此成員函式建立 rebar。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>參數  
 *pParentWnd*  
 指標`CWnd`其 Windows 視窗中是 [狀態] 列的父代的物件。 通常框架視窗。  
  
 *dwCtrlStyle*  
 Rebar 控制項樣式。 根據預設， **RBS_BANDBORDERS**，它會顯示縮小範圍，來分隔相鄰的群組列的 rebar 控制項中的行。 請參閱[Rebar 控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb774377)樣式清單的 Windows SDK 中。  
  
 *dwStyle*  
 Rebar 的視窗樣式。  
  
 *nID*  
 Rebar 的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[CReBar::AddBar](#addbar)。  
  
##  <a name="getrebarctrl"></a>  Crebar:: Getrebarctrl  
 此成員函式可讓您直接存取基礎的通用控制項。  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 若要參考[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)物件。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以善用 Windows rebar 通用控制項，自訂您 rebar 的功能。 當您呼叫`GetReBarCtrl`，它會傳回參考物件至`CReBarCtrl`物件，以便您可以使用任一組成員函式。  
  
 如需有關使用`CReBarCtrl`若要自訂您 rebar，請參閱[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MFCIE](../../visual-cpp-samples.md)   
 [CControlBar 類別](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



