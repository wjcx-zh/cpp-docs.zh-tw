---
title: CMFCPreviewCtrlImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29632784248d624f184550f0c598d05cd26b85cf
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079541"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 類別

這個類別會實作放置在 Shell for Rich Preview 提供的主視窗的視窗。

## <a name="syntax"></a>語法

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs 預覽控制項物件。|
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|建構預覽控制項物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::Create](#create)|多載。 由建立 Windows 視窗的豐富預覽處理常式呼叫。|
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|需要終結此控制項時，由豐富的預覽處理常式呼叫。|
|[CMFCPreviewCtrlImpl::Focus](#focus)|設定輸入這個控制項的焦點。|
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|傳回連接到此預覽控制項的文件。|
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|會告知此控制項重繪。|
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|呼叫預覽處理常式建立文件實作與預覽控制項之間的關聯性。|
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|設定這個控制項的新父系。|
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|豐富的預覽處理常式時呼叫它需要設定視覺效果豐富的預覽的內容。|
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|設定這個控制項的新週框矩形。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|由架構呼叫以呈現預覽。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|預覽視窗的背景色彩。|
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|預覽視窗的文字色彩。|
|[CMFCPreviewCtrlImpl::m_font](#m_font)|用來在 [預覽] 視窗中顯示文字的字型。|
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|內容控制項中可預覽的文件指標。|

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a> CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl

建構預覽控制項物件。

### <a name="syntax"></a>語法

CMFCPreviewCtrlImpl();

## <a name="create"></a> CMFCPreviewCtrlImpl::Create

多載。 由建立 Windows 視窗的豐富預覽處理常式呼叫。

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

*hWndParent*<br/>
提供由 Shell for Rich Preview 主機視窗的控制代碼。

*中華人民共和國*<br/>
指定的初始大小和視窗的位置。

*pContext*<br/>
建立內容的指標。

### <a name="return-value"></a>傳回值

如果作業成功，則為 TRUE，否則為 FALSE。

## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy

需要終結此控制項時，由豐富的預覽處理常式呼叫。

### <a name="syntax"></a>語法

```
virtual void Destroy();
```

## <a name="dopaint"></a> CMFCPreviewCtrlImpl::DoPaint

由架構呼叫以呈現預覽。

### <a name="syntax"></a>語法

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>參數

*pDC*<br/>
要繪製的裝置內容指標。

## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus

設定輸入這個控制項的焦點。

### <a name="syntax"></a>語法

```
virtual void Focus();
```

## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument

傳回連接到此預覽控制項的文件。

### <a name="syntax"></a>語法

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>傳回值

文件，其內容預覽控制項中的指標。

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor

[預覽] 視窗的背景色彩。

### <a name="syntax"></a>語法

```
COLORREF m_clrBackColor;
```

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor

[預覽] 視窗的文字色彩。

### <a name="syntax"></a>語法

```
COLORREF m_clrTextColor;
```

## <a name="m_font"></a> CMFCPreviewCtrlImpl::m_font 字型會用來在 [預覽] 視窗中顯示文字。

### <a name="syntax"></a>語法

```
CFont m_font;
```

## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument

內容控制項中可預覽的文件指標。

### <a name="syntax"></a>語法

```
ATL::IDocument* m_pDocument;
```

## <a name="redraw"></a> CMFCPreviewCtrlImpl::Redraw

會告知此控制項重繪。

### <a name="syntax"></a>語法

```
virtual void Redraw();
```

## <a name="setdocument"></a> CMFCPreviewCtrlImpl::SetDocument

呼叫預覽處理常式建立文件實作與預覽控制項之間的關聯性。

### <a name="syntax"></a>語法

```
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>參數

*pDocument*<br/>
文件實作指標。

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost

設定這個控制項的新父系。

### <a name="syntax"></a>語法

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
新的父視窗的控制代碼。

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals

豐富的預覽處理常式時呼叫它需要設定視覺效果豐富的預覽的內容。

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
預覽視窗的背景色彩。

*clrText*<br/>
預覽視窗的文字色彩。

*plf*<br/>
用來在 [預覽] 視窗中顯示文字的字型。

##  <a name="setrect"></a> CMFCPreviewCtrlImpl::SetRect

設定這個控制項的新週框矩形。

### <a name="syntax"></a>語法

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>參數

*中華人民共和國*<br/>
指定新的大小和預覽控制項的位置。

*bRedraw*<br/>
指定是否應該重新繪製控制項。

### <a name="remarks"></a>備註

通常主控制項調整大小時，會設定新的週框矩形。

## <a name="dtor"></a> CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl

Destructs 預覽控制項物件。

### <a name="syntax"></a>語法

```
virtual ~CMFCPreviewCtrlImpl();
```

