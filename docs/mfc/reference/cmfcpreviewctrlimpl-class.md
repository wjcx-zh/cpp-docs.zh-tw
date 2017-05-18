---
title: "CMFCPreviewCtrlImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCPreviewCtrlImpl class
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
caps.latest.revision: 28
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b3ccd0d6e03f652798b45ac35d36f8bc2f63e048
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 類別
這個類別會實作放置在 Shell for Rich Preview 提供之主機視窗的視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCPreviewCtrlImpl : public CWnd;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl](#dtor)|Destructs 預覽控制項物件。|  
|[CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl](#cmfcpreviewctrlimpl)|建構預覽控制項物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::Create](#create)|多載。 若要建立 Windows 視窗的豐富預覽處理常式呼叫。|  
|[CMFCPreviewCtrlImpl::Destroy](#destroy)|要終結這個控制項需要時，由豐富的預覽處理常式呼叫。|  
|[CMFCPreviewCtrlImpl::Focus](#focus)|設定輸入這個控制項焦點。|  
|[CMFCPreviewCtrlImpl::GetDocument](#getdocument)|傳回連接到此預覽控制項的文件。|  
|[CMFCPreviewCtrlImpl::Redraw](#redraw)|說明此控制項重繪。|  
|[CMFCPreviewCtrlImpl::SetDocument](#setdocument)|呼叫預覽處理常式建立文件實作與預覽控制項之間的關聯性。|  
|[CMFCPreviewCtrlImpl::SetHost](#sethost)|設定新的父項對這個控制項。|  
|[CMFCPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|豐富的預覽處理常式時呼叫必須設定視覺效果豐富的預覽的內容。|  
|[CMFCPreviewCtrlImpl::SetRect](#setrect)|設定這個控制項的新周框矩形。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::DoPaint](#dopaint)|呈現預覽架構呼叫。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCPreviewCtrlImpl::m_clrBackColor](#m_clrbackcolor)|預覽視窗的背景色彩。|  
|[CMFCPreviewCtrlImpl::m_clrTextColor](#m_clrtextcolor)|預覽視窗的文字色彩。|  
|[CMFCPreviewCtrlImpl::m_font](#m_font)|用來在預覽視窗中顯示文字的字型。|  
|[CMFCPreviewCtrlImpl::m_pDocument](#m_pdocument)|內容控制項中可預覽的文件指標。|  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h    
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPreviewCtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimpl"></a>CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
建構預覽控制項物件。

### <a name="syntax"></a>語法
CMFCPreviewCtrlImpl();  

## <a name="create"></a>CMFCPreviewCtrlImpl::Create
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
 `hWndParent`  
 提供在 shell for Rich Preview 主應用程式視窗的控制代碼。  
  
 `prc`  
 指定的初始大小和視窗的位置。  
  
 `pContext`  
 建立內容的指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果建立成功。否則`FALSE`。  
  
## <a name="destroy"></a>CMFCPreviewCtrlImpl::Destroy
要終結這個控制項需要時，由豐富的預覽處理常式呼叫。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void Destroy();  
```  
  
## <a name="dopaint"></a>CMFCPreviewCtrlImpl::DoPaint  
呈現預覽架構呼叫。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void DoPaint(  
   CPaintDC* pDC  
);  
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 要繪製的裝置內容指標。  


## <a name="focus"></a>CMFCPreviewCtrlImpl::Focus  
設定輸入這個控制項焦點。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void Focus();  
```  
## <a name="getdocument"></a>CMFCPreviewCtrlImpl::GetDocument
傳回連接到此預覽控制項的文件。  
  
### <a name="syntax"></a>語法  
  
```  
ATL::IDocument* GetDocument();  
```  
  
### <a name="return-value"></a>傳回值  
 文件，其內容控制項中可預覽指標。

## <a name="m_clrbackcolor"></a>CMFCPreviewCtrlImpl::m_clrBackColor  
預覽視窗的背景色彩。  
  
### <a name="syntax"></a>語法  
  
```  
COLORREF m_clrBackColor;  
```  

## <a name="m_clrtextcolor"></a>CMFCPreviewCtrlImpl::m_clrTextColor
預覽視窗的文字色彩。  
  
### <a name="syntax"></a>語法  
  
```  
COLORREF m_clrTextColor;  
```  
## <a name="m_font"></a>CMFCPreviewCtrlImpl::m_font 用來在預覽視窗中顯示文字的字型。  
  
### <a name="syntax"></a>語法  
  
```  
CFont m_font;  
```  
## <a name="m_pdocument"></a>CMFCPreviewCtrlImpl::m_pDocument  
內容控制項中可預覽的文件指標。  
  
### <a name="syntax"></a>語法  
  
```  
ATL::IDocument* m_pDocument;  
```  

## <a name="redraw"></a>CMFCPreviewCtrlImpl::Redraw  
說明此控制項重繪。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void Redraw();  
```  
## <a name="setdocument"></a>CMFCPreviewCtrlImpl::SetDocument 
呼叫預覽處理常式建立文件實作與預覽控制項之間的關聯性。  
  
### <a name="syntax"></a>語法  
  
```  
void SetDocument(  
   IDocument* pDocument  
);  
```  
  
### <a name="parameters"></a>參數  
 `pDocument`  
 文件實作指標。  

## <a name="sethost"></a>CMFCPreviewCtrlImpl::SetHost  
設定新的父項對這個控制項。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void SetHost(  
   HWND hWndParent  
);  
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 新的父視窗控制代碼。  

## <a name="setpreviewvisuals"></a>CMFCPreviewCtrlImpl::SetPreviewVisuals  
豐富的預覽處理常式時呼叫必須設定視覺效果豐富的預覽的內容。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void SetPreviewVisuals(  
   COLORREF clrBack,  
   COLORREF clrText,  
   const LOGFONTW *plf  
);  
```  
  
### <a name="parameters"></a>參數  
 `clrBack`  
 預覽視窗的背景色彩。  
  
 `clrText`  
 預覽視窗的文字色彩。  
  
 `plf`  
 用來在預覽視窗中顯示文字的字型。 

##  <a name="setrect"></a>CMFCPreviewCtrlImpl::SetRect  
設定這個控制項的新周框矩形。  
  
### <a name="syntax"></a>語法  
  
```  
virtual void SetRect(  
   const RECT* prc,  
   BOOL bRedraw  
);  
```  
  
### <a name="parameters"></a>參數  
 `prc`  
 指定新的大小和預覽控制項的位置。  
  
 `bRedraw`  
 指定是否應該重新繪製控制項。  
  
### <a name="remarks"></a>備註  
 通常主控制項的大小時，會設定新周框矩形。  

## <a name="dtor"></a>CMFCPreviewCtrlImpl:: ~ CMFCPreviewCtrlImpl  
Destructs 預覽控制項物件。  
  
### <a name="syntax"></a>語法  
  
```  
virtual ~CMFCPreviewCtrlImpl();  
```  
  

