---
title: CMFCPreviewCtrlImpl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: 0c0a594a84b45ce7bf6f2c2fa5d1a547fa10eaa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751843"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 類別

此類實現放置在「豐富預覽」的 Shell 提供的主機視窗中的視窗。

## <a name="syntax"></a>語法

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC預覽CtrlImpl::_CMFC預覽CtrlImpl](#dtor)|析構預覽控件物件。|
|[CMFC 預覽 Ctrlimpl::CMFC 預覽Ctrlimpl](#cmfcpreviewctrlimpl)|構造預覽控件物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 預覽 Ctrlimpl::創建](#create)|已多載。 由「豐富預覽」處理程式呼叫以創建 Windows 視窗。|
|[CMFC預覽CtrlImpl::D](#destroy)|當需要銷毀此控件時,由富預覽處理程序調用。|
|[CMFC預覽CtrlImpl::焦點](#focus)|對這個控制項設定輸入焦點。|
|[CMFC預覽Ctrlimpl::取得文檔](#getdocument)|返回連接到此預覽控制項的文件。|
|[CMFC 預覽 Ctrlimpl::重繪](#redraw)|告訴此控制件重繪。|
|[CMFC 預覽 Ctrlimpl::設定文檔](#setdocument)|由預覽處理程式呼叫以創建文件實現和預覽控制項之間的關係。|
|[CMFC 預覽 Ctrlimpl::SetHost](#sethost)|為此控件設置新父級。|
|[CMFC 預覽 CtrlImpl::設定預覽視覺物件](#setpreviewvisuals)|當需要設置富預覽內容的可視物件時,由"豐富預覽"處理程序調用。|
|[CMFC 預覽 Ctrlimpl::SetRect](#setrect)|為此控件設置一個新的邊界矩形。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC預覽CtrlImpl::DoPaint](#dopaint)|由框架調用以呈現預覽。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC 預覽CtrlImpl::m_clrBackColor](#m_clrbackcolor)|預覽視窗的背景顏色。|
|[CMFC 預覽CtrlImpl::m_clrTextColor](#m_clrtextcolor)|預覽視窗的文字顏色。|
|[CMFC預覽CtrlImpl::m_font](#m_font)|用於在預覽視窗中顯示文本的字型。|
|[CMFC 預覽CtrlImpl::m_pDocument](#m_pdocument)|指向在控制項中預覽其內容的文件的指標。|

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFC 預覽CtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFC 預覽 Ctrlimpl::CMFC 預覽Ctrlimpl

構造預覽控件物件。

### <a name="syntax"></a>語法

CMFC預覽CtrlImpl();

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFC 預覽 Ctrlimpl::創建

已多載。 由「豐富預覽」處理程式呼叫以創建 Windows 視窗。

### <a name="syntax"></a>語法

```
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc
);
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc,
   CCreateContext* pContext
);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
用於富預覽的 Shell 提供的主機視窗的句柄。

*中國*<br/>
指定視窗的初始大小和位置。

*pContext*<br/>
指向創建上下文的指標。

### <a name="return-value"></a>傳回值

如果作業成功，則為 TRUE，否則為 FALSE。

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFC預覽CtrlImpl::D

當需要銷毀此控件時,由富預覽處理程序調用。

### <a name="syntax"></a>語法

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFC預覽CtrlImpl::DoPaint

由框架調用以呈現預覽。

### <a name="syntax"></a>語法

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>參數

*pDC*<br/>
指向用於繪製的設備上下文的指標。

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFC預覽CtrlImpl::焦點

對這個控制項設定輸入焦點。

### <a name="syntax"></a>語法

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFC預覽Ctrlimpl::取得文檔

返回連接到此預覽控制項的文件。

### <a name="syntax"></a>語法

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>傳回值

指向文檔的指標,其內容在控件中預覽。

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFC 預覽CtrlImpl::m_clrBackColor

預覽視窗的背景顏色。

### <a name="syntax"></a>語法

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFC 預覽CtrlImpl::m_clrTextColor

預覽視窗的文字顏色。

### <a name="syntax"></a>語法

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFC預覽CtrlImpl::m_font字體用於在預覽視窗中顯示文本。

### <a name="syntax"></a>語法

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFC 預覽CtrlImpl::m_pDocument

指向在控制項中預覽其內容的文件的指標。

### <a name="syntax"></a>語法

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFC 預覽 Ctrlimpl::重繪

告訴此控制件重繪。

### <a name="syntax"></a>語法

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFC 預覽 Ctrlimpl::設定文檔

由預覽處理程式呼叫以創建文件實現和預覽控制項之間的關係。

### <a name="syntax"></a>語法

```cpp
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>參數

*pDocument*<br/>
指向文檔實現的指標。

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFC 預覽 Ctrlimpl::SetHost

為此控件設置新父級。

### <a name="syntax"></a>語法

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
新父視窗的句柄。

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFC 預覽 CtrlImpl::設定預覽視覺物件

當需要設置富預覽內容的可視物件時,由"豐富預覽"處理程序調用。

### <a name="syntax"></a>語法

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>參數

*clrBack*<br/>
預覽視窗的背景顏色。

*clrText*<br/>
預覽視窗的文字顏色。

*plf*<br/>
用於在預覽視窗中顯示文本的字型。

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFC 預覽 Ctrlimpl::SetRect

為此控件設置一個新的邊界矩形。

### <a name="syntax"></a>語法

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>參數

*中國*<br/>
指定預覽控制件的新大小和位置。

*bredraw*<br/>
指定是否應重繪控制件。

### <a name="remarks"></a>備註

通常,在調整主機控件大小時,將設置一個新的邊界矩形。

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFC預覽CtrlImpl::_CMFC預覽CtrlImpl

析構預覽控件物件。

### <a name="syntax"></a>語法

```
virtual ~CMFCPreviewCtrlImpl();
```
