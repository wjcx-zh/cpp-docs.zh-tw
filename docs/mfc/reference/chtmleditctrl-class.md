---
title: "CHtmlEditCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl class
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: 22
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4aca52508663e94ee9a1b55843ad05613aa40b0b
ms.lasthandoff: 02/24/2017

---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl 類別
在 MFC 視窗中提供 WebBrowser ActiveX 控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|建構 `CHtmlEditCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|建立 WebBrowser ActiveX 控制項並將它附加`CHtmlEditCtrl`物件。 此函式會自動變成 WebBrowser ActiveX 控制項，在編輯模式。|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|擷取[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)內含的 WebBrowser 控制項中目前載入的文件上的介面。|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|擷取預設文件載入所包含的 WebBrowser 控制項中的 URL。|  
  
## <a name="remarks"></a>備註  
 建立後，裝載的 WebBrowser 控制項自動進入編輯模式。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>需求  
 **Header:** afxhtml.h  
  
##  <a name="a-namechtmleditctrla--chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl  
 建構 `CHtmlEditCtrl` 物件。  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="a-namecreatea--chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Create  
 建立 WebBrowser ActiveX 控制項並將它附加`CHtmlEditCtrl`物件。 WebBrowser ActiveX 控制項自動瀏覽至預設文件，並將其放在編輯模式，此函式。  
  
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
 `lpszWindowName`  
 不使用這個參數。  
  
 `dwStyle`  
 不使用這個參數。  
  
 `rect`  
 指定控制項的大小和位置。  
  
 `pParentWnd`  
 指定控制項的父視窗。 它不得為**NULL**。  
  
 `nID`  
 指定控制項的 id。  
  
 `pContext`  
 不使用這個參數。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
##  <a name="a-namegetdhtmldocumenta--chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument  
 擷取[IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx)內含的 WebBrowser 控制項中目前載入的文件上的介面  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>參數  
 `ppDocument`  
 文件介面中。  
  
##  <a name="a-namegetstartdocumenta--chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument  
 擷取預設文件載入所包含的 WebBrowser 控制項中的 URL。  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)


