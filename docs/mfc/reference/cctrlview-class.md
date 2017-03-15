---
title: "CCtrlView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCtrlView
dev_langs:
- C++
helpviewer_keywords:
- views, and common controls
- controls [MFC], common
- CCtrlView class
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 569044de59dc3ccd73157abc86855beef57cb558
ms.lasthandoff: 02/24/2017

---
# <a name="cctrlview-class"></a>CCtrlView 類別
調整文件檢視架構來配合 Windows 98 和 Windows NT 3.51 版 (含) 以後版本支援的通用控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CCtrlView : public CView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](#cctrlview)|建構 `CCtrlView` 物件。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CCtrlView::OnDraw](#ondraw)|使用指定的裝置內容繪製架構所呼叫。|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|在建立附加至此 `CCtrlView` 物件的 Windows 視窗前呼叫。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|包含檢視類別的預設樣式。|  
|[CCtrlView::m_strClass](#m_strclass)|包含檢視類別的 Windows 類別名稱。|  
  
## <a name="remarks"></a>備註  
 類別`CCtrlView`和其衍生項目， [CEditView](../../mfc/reference/ceditview-class.md)， [CListView](../../mfc/reference/clistview-class.md)， [CTreeView](../../mfc/reference/ctreeview-class.md)，和[CRichEditView](../../mfc/reference/cricheditview-class.md)，調整為新的通用控制項版本支援 Windows 95/98 和 Windows NT 3.51 和更新版本的文件檢視架構。 如需有關文件檢視架構的詳細資訊，請參閱[文件/檢視架構](../../mfc/document-view-architecture.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecctrlviewa--cctrlviewcctrlview"></a><a name="cctrlview"></a>CCtrlView::CCtrlView  
 建構 `CCtrlView` 物件。  
  
```  
CCtrlView(
    LPCTSTR lpszClass,  
    DWORD dwStyle);
```  
  
### <a name="parameters"></a>參數  
 `lpszClass`  
 檢視類別的 Windows 類別名稱。  
  
 `dwStyle`  
 檢視類別的樣式。  
  
### <a name="remarks"></a>備註  
 建立新的框架視窗，或分隔視窗時，架構會呼叫建構函式。 覆寫[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)文件連結之後初始化檢視。 呼叫[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)來建立視窗物件。  
  
##  <a name="a-namemstrclassa--cctrlviewmstrclass"></a><a name="m_strclass"></a>CCtrlView::m_strClass  
 包含檢視類別的 Windows 類別名稱。  
  
```  
CString m_strClass;  
```  
  
##  <a name="a-namemdwdefaultstylea--cctrlviewmdwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle  
 包含檢視類別的預設樣式。  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>備註  
 建立視窗時，會套用此樣式。  
  
##  <a name="a-nameondrawa--cctrlviewondraw"></a><a name="ondraw"></a>CCtrlView::OnDraw  
 若要繪製的內容架構呼叫`CCtrlView`物件使用指定的裝置內容。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 發生在繪製的裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 `OnDraw`通常會呼叫傳遞所指定的螢幕裝置內容的螢幕上的`pDC`。  
  
##  <a name="a-nameprecreatewindowa--cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CCtrlView::PreCreateWindow  
 在建立附加至此 `CWnd` 物件的 Windows 視窗前呼叫。  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>參數  
 *cs*  
 A [CREATESTRUCT](http://msdn.microsoft.com/library/windows/desktop/ms632603)結構。  
  
### <a name="return-value"></a>傳回值  
 非零，如果應該繼續建立視窗。0 表示建立失敗。  
  
### <a name="remarks"></a>備註  
 永遠不會直接呼叫此函式。  
  
 此函式的預設實作會檢查**NULL**視窗類別名稱並換成適當的預設值。 覆寫此成員函式，以修改`CREATESTRUCT`結構建立視窗之前。  
  
 每個類別衍生自`CCtrlView`它自己的功能將其覆寫`PreCreateWindow`。 根據設計，這些衍生的`PreCreateWindow`未提供說明。 若要判斷用於每個類別和樣式之間的相互依存性的樣式，您可以檢查您的應用程式基底類別的 MFC 原始程式碼。 如果您選擇覆寫`PreCreateWindow`，您可以判斷您的應用程式基底類別中的樣式是否提供您需要使用 MFC 原始程式碼中所收集資訊的功能。  
  
 如需有關如何變更視窗樣式的詳細資訊，請參閱[變更 MFC 所建立的視窗樣式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CView 類別](../../mfc/reference/cview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CTreeView 類別](../../mfc/reference/ctreeview-class.md)   
 [CListView 類別](../../mfc/reference/clistview-class.md)   
 [CRichEditView 類別](../../mfc/reference/cricheditview-class.md)

