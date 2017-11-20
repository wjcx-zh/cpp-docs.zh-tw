---
title: "CPaintDC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
dev_langs: C++
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 58d1c1ec052c399cf56cd145e7ee06f52483661e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cpaintdc-class"></a>CPaintDC 類別
裝置內容類別衍生自[CDC](../../mfc/reference/cdc-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CPaintDC : public CDC  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CPaintDC::CPaintDC](#cpaintdc)|建構`CPaintDC`連線到指定[CWnd](../../mfc/reference/cwnd-class.md)。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPaintDC::m_ps](#m_ps)|包含[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)用來繪製工作區。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|`HWND`這個`CPaintDC`附加物件。|  
  
## <a name="remarks"></a>備註  
 它會執行[cwnd:: Beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)在建構階段和[CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint)在解構階段。  
  
 A`CPaintDC`物件只可在回應時[WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213)訊息，通常會在您`OnPaint`訊息處理常式成員函式。  
  
 如需有關使用`CPaintDC`，請參閱[裝置內容](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cpaintdc"></a>CPaintDC::CPaintDC  
 建構`CPaintDC`物件，準備應用程式視窗，以進行繪製，並將[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)結構[m_ps](#m_ps)成員變數。  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 指向`CWnd`物件`CPaintDC`所屬的物件。  
  
### <a name="remarks"></a>備註  
 例外狀況 (型別`CResourceException`) 則會擲回 Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)呼叫就會失敗。 裝置內容可能無法使用，如果 Windows 已有已配置所有其可用的裝置內容。 您的應用程式競爭的五個一般顯示內容可用在任何指定的時間，在 Windows 下。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CPaintDC::m_hWnd  
 `HWND`這個`CPaintDC`附加物件。  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>備註  
 `m_hWnd`這是受保護的型別變數`HWND`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>CPaintDC::m_ps  
 `m_ps`這類型的公用成員變數[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)。  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>備註  
 它是`PAINTSTRUCT`傳遞至和填寫該[cwnd:: Beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)。  
  
 `PAINTSTRUCT`包含應用程式用來繪製視窗相關聯的工作區資訊`CPaintDC`物件。  
  
 請注意，您可以存取的裝置內容控制代碼，透過`PAINTSTRUCT`。 不過，您可以存取的控制代碼更直接透過`m_hDC`成員變數，`CPaintDC`繼承自`CDC`。  
  
### <a name="example"></a>範例  
  請參閱範例的[CPaintDC::m_hWnd](#m_hwnd)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



