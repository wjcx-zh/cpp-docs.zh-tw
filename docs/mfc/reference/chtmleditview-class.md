---
title: "CHtmlEditView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
dev_langs: C++
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 98964a48be8b8c36a3d6d5bd708a51b9963ae105
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="chtmleditview-class"></a>CHtmlEditView 類別
在 MFC 的文件/檢視架構內容中提供 WebBrowser 編輯平台的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|建構 `CHtmlEditView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHtmlEditView::Create](#create)|建立新的視窗物件。|  
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|傳回**IHTMLDocument2**介面上目前文件。|  
|[CHtmlEditView::GetStartDocument](#getstartdocument)|擷取這個檢視的預設文件名稱。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## <a name="requirements"></a>需求  
 **Header:** afxhtml.h  
  
##  <a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView  
 建構 `CHtmlEditView` 物件。  
  
```  
CHtmlEditView();
```  
  
##  <a name="create"></a>CHtmlEditView::Create  
 建立新的視窗物件。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszClassName`  
 指向以 null 結束的字元字串，Windows 類別命名。 類別名稱可以是任何名稱登錄與[AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)全域函式或**RegisterClass** Windows 函式。 如果**NULL**，會使用預先定義的預設[CFrameWnd](../../mfc/reference/cframewnd-class.md)屬性。  
  
 `lpszWindowName`  
 指向以 null 結束的字元字串，表示視窗名稱。  
  
 `dwStyle`  
 指定視窗的樣式屬性。 根據預設， **WS_VISIBLE**和**WS_CHILD**設定視窗樣式。  
  
 `rect`  
 若要參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定的大小和視窗的位置。 `rectDefault`值，可讓 Windows，指定新的視窗位置與大小。  
  
 `pParentWnd`  
 控制項的父視窗指標。  
  
 `nID`  
 檢視的識別碼。 根據預設，設定為**AFX_IDW_PANE_FIRST**。  
  
 `pContext`  
 指標[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)。 **NULL**預設。  
  
### <a name="remarks"></a>備註  
 這個方法也會呼叫包含的 WebBrowser**瀏覽**方法以載入預設文件 (請參閱[CHtmlEditView::GetStartDocument](#getstartdocument))。  
  
##  <a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument  
 傳回**IHTMLDocument2**介面上目前文件。  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>參數  
 `ppDocument`  
 [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)介面。  
  
##  <a name="getstartdocument"></a>CHtmlEditView::GetStartDocument  
 擷取這個檢視的預設文件名稱。  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>請參閱  
 [HTMLEdit 範例](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


