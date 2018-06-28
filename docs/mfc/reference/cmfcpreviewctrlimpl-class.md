---
title: CMFCPreviewCtrlImpl 類別 |Microsoft 文件
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
ms.openlocfilehash: a94ad813ff72eaed2642e9c78a098b999bf128fa
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040073"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 類別
這個類別會實作會放在 Shell for Rich Preview 提供主控視窗的視窗。  
  
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
|[CMFCPreviewCtrlImpl::Create](#create)|多載。 若要建立 Windows 視窗的豐富預覽處理常式呼叫。|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|需要終結此控制項時呼叫的豐富預覽處理常式。|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|設定輸入這個控制項的焦點。|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|傳回連接到此預覽控制文件。|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|會告知此控制項重繪。|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|若要建立的文件實作預覽控制項之間的關聯性的預覽處理常式呼叫。|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|設定對這個控制項的新父系。|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|由呼叫的豐富預覽處理常式需要設定豐富的預覽的視覺效果時內容。|  
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
|[CMFCPreviewCtrlImpl::m_font](#m_font)|用來在預覽視窗中顯示文字的字型。|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|在控制項中可預覽其內容的文件指標。|  
  
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
多載。 若要建立 Windows 視窗的豐富預覽處理常式呼叫。  
  
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
 *hWndParent*  
 在 Shell for Rich Preview 提供主控視窗控制代碼。  
  
 *中國*  
 指定的初始大小和視窗的位置。  
  
 *pContext*  
 建立內容的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果作業成功。否則`FALSE`。  
  
## <a name="destroy"></a> CMFCPreviewCtrlImpl::Destroy
需要終結此控制項時呼叫的豐富預覽處理常式。  
  
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
 *pDC*  
 繪製的裝置內容的指標。  


## <a name="focus"></a> CMFCPreviewCtrlImpl::Focus  
設定輸入這個控制項的焦點。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a> CMFCPreviewCtrlImpl::GetDocument
傳回連接到此預覽控制文件。  
  
### <a name="syntax"></a>語法  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>傳回值  
 文件中，控制項中可預覽其內容指標。

## <a name="m_clrbackcolor"></a> CMFCPreviewCtrlImpl::m_clrBackColor  
[預覽] 視窗的背景色彩。  
  
### <a name="syntax"></a>語法  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a> CMFCPreviewCtrlImpl::m_clrTextColor
預覽視窗的文字色彩。  
  
### <a name="syntax"></a>語法  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a> CMFCPreviewCtrlImpl::m_font 用來在預覽視窗中顯示文字的字型。  
  
### <a name="syntax"></a>語法  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a> CMFCPreviewCtrlImpl::m_pDocument  
在控制項中可預覽其內容的文件指標。  
  
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
若要建立的文件實作預覽控制項之間的關聯性的預覽處理常式呼叫。  
  
### <a name="syntax"></a>語法  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>參數  
 *pDocument*  
 文件實作指標。  

## <a name="sethost"></a> CMFCPreviewCtrlImpl::SetHost  
設定對這個控制項的新父系。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>參數  
 *hWndParent*  
 新的父視窗控制代碼。  

## <a name="setpreviewvisuals"></a> CMFCPreviewCtrlImpl::SetPreviewVisuals  
由呼叫的豐富預覽處理常式需要設定豐富的預覽的視覺效果時內容。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>參數  
 *clrBack*  
 預覽視窗的背景色彩。  
  
 *clrText*  
 預覽視窗的文字色彩。  
  
 *plf*  
 用來在預覽視窗中顯示文字的字型。 

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
 *中國*  
 指定新的大小和預覽控制項的位置。  
  
 *bRedraw*  
 指定是否應該重繪控制項。  
  
### <a name="remarks"></a>備註  
 通常主控制項重新調整大小時，會設定新週框矩形。  

## <a name="dtor"></a> CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destructs 預覽控制項物件。  
  
### <a name="syntax"></a>語法  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  
