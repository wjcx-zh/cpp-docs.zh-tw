---
title: CHtmlEditCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cc8cdc389edc8abbc424ec8277f759e7f3d81bb
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338564"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl 類別
在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|建構 `CHtmlEditCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|建立 WebBrowser ActiveX 控制項，並將它附加至`CHtmlEditCtrl`物件。 此函式會自動會將 WebBrowser ActiveX 控制項進入編輯模式。|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|擷取[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)內含的 WebBrowser 控制項中目前載入文件上的介面。|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|擷取預設文件載入所包含的 WebBrowser 控制項中的 URL。|  
  
## <a name="remarks"></a>備註  
 在建立之後，裝載的 WebBrowser 控制項自動放入編輯模式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>需求  
 **Header:** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl  
 建構 `CHtmlEditCtrl` 物件。  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>  CHtmlEditCtrl::Create  
 建立 WebBrowser ActiveX 控制項，並將它附加至`CHtmlEditCtrl`物件。 WebBrowser ActiveX 控制項自動瀏覽至預設文件，則會放在編輯模式，此函式。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpszWindowName*  
 不使用這個參數。  
  
 *cheaderctrl:: Create*  
 不使用這個參數。  
  
 *rect*  
 指定控制項的大小和位置。  
  
 *pParentWnd*  
 指定控制項的父視窗。 它必須不是 NULL。  
  
 *nID*  
 指定控制項的識別碼。  
  
 *pContext*  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument  
 擷取[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)內含的 WebBrowser 控制項中目前載入文件上的介面  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>參數  
 *ppDocument*  
 文件介面中。  
  
##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument  
 擷取預設文件載入所包含的 WebBrowser 控制項中的 URL。  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)

