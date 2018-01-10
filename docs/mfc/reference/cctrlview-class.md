---
title: "CCtrlView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
dev_langs: C++
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 484abaf5344400e03b53038d2c137497c202345f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cctrlview-class"></a>CCtrlView 類別
調整文件檢視架構來配合 Windows 98 和 Windows NT 3.51 版 (含) 以後版本支援的通用控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CCtrlView : public CView  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](#cctrlview)|建構 `CCtrlView` 物件。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CCtrlView::OnDraw](#ondraw)|由架構呼叫以繪製使用指定的裝置內容。|  
|[CCtrlView::PreCreateWindow](#precreatewindow)|在建立附加至此 `CCtrlView` 物件的 Windows 視窗前呼叫。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|包含檢視類別的預設樣式。|  
|[CCtrlView::m_strClass](#m_strclass)|包含檢視類別的 Windows 類別名稱。|  
  
## <a name="remarks"></a>備註  
 類別`CCtrlView`和其衍生項目， [CEditView](../../mfc/reference/ceditview-class.md)， [CListView](../../mfc/reference/clistview-class.md)， [CTreeView](../../mfc/reference/ctreeview-class.md)，和[CRichEditView](../../mfc/reference/cricheditview-class.md)，調整與新的通用控制項的文件檢視架構支援 Windows 95/98、 Windows NT 3.51 及更新版本。 如需有關文件檢視架構的詳細資訊，請參閱[文件/檢視架構](../../mfc/document-view-architecture.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cctrlview"></a>CCtrlView::CCtrlView  
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
 建立新的框架視窗或分隔視窗時，架構會呼叫建構函式。 覆寫[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)初始化之後附加文件的檢視。 呼叫[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)建立 Windows 物件。  
  
##  <a name="m_strclass"></a>CCtrlView::m_strClass  
 包含檢視類別的 Windows 類別名稱。  
  
```  
CString m_strClass;  
```  
  
##  <a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle  
 包含檢視類別的預設樣式。  
  
```  
DWORD m_dwDefaultStyle;  
```  
  
### <a name="remarks"></a>備註  
 建立視窗時，會套用此樣式。  
  
##  <a name="ondraw"></a>CCtrlView::OnDraw  
 由架構呼叫以繪製的內容`CCtrlView`物件使用指定的裝置內容。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 繪圖發生在哪個裝置內容的指標。  
  
### <a name="remarks"></a>備註  
 `OnDraw`通常會呼叫傳遞螢幕裝置內容所指定的螢幕上的`pDC`。  
  
##  <a name="precreatewindow"></a>CCtrlView::PreCreateWindow  
 在建立附加至此 `CWnd` 物件的 Windows 視窗前呼叫。  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>參數  
 *cs*  
 A [CREATESTRUCT](http://msdn.microsoft.com/library/windows/desktop/ms632603)結構。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果應該繼續建立視窗。0，表示建立失敗。  
  
### <a name="remarks"></a>備註  
 永遠不會直接呼叫此函式。  
  
 此函式的預設實作會檢查**NULL**視窗類別名稱並換成適當的預設值。 若要修改此成員函式會覆寫`CREATESTRUCT`結構建立視窗之前。  
  
 每個類別衍生自`CCtrlView`將自己的功能加入至其覆寫`PreCreateWindow`。 根據設計，這些衍生的`PreCreateWindow`未記載。 若要判斷用於每個類別和樣式之間的相依性的樣式，您可以檢查您的應用程式基底類別的 MFC 原始程式碼。 如果您選擇覆寫`PreCreateWindow`，您可以判斷您的應用程式基底類別中使用的樣式是否提供您需要藉由從 MFC 原始程式碼所收集資訊的功能。  
  
 如需有關如何變更視窗樣式的詳細資訊，請參閱[變更 MFC 所建立的視窗樣式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。  
  
## <a name="see-also"></a>請參閱  
 [CView 類別](../../mfc/reference/cview-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CTreeView 類別](../../mfc/reference/ctreeview-class.md)   
 [CListView 類別](../../mfc/reference/clistview-class.md)   
 [CRichEditView 類別](../../mfc/reference/cricheditview-class.md)
