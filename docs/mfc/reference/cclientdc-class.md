---
title: "CClientDC 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CClientDC
dev_langs:
- C++
helpviewer_keywords:
- CClientDC class
- device contexts, client area
- client-area device context
- CDC class, device contexts for client areas
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 619bed4d31994bde8464ad710e9f050d6ba0696a
ms.lasthandoff: 02/24/2017

---
# <a name="cclientdc-class"></a>CClientDC 類別
呼叫 Windows 函式會負責[GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)在建構階段和[ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920)在解構階段。  
  
## <a name="syntax"></a>語法  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|建構`CClientDC`物件連接到`CWnd`。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|`HWND`之視窗的`CClientDC`有效。|  
  
## <a name="remarks"></a>備註  
 這表示，與相關聯的裝置內容`CClientDC`物件為視窗的用戶端區域。  
  
 如需有關`CClientDC`，請參閱[裝置內容](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="a-namecclientdca--cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC::CClientDC  
 建構`CClientDC`物件存取的工作區[CWnd](../../mfc/reference/cwnd-class.md)指向`pWnd`。  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 視窗的裝置內容物件將會存取其工作區中。  
  
### <a name="remarks"></a>備註  
 建構函式會呼叫 Windows 函式[GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)。  
  
 例外狀況 (型別`CResourceException`) 則會擲回 Windows`GetDC`呼叫就會失敗。 裝置內容可能無法使用，如果 Windows 有已配置所有其可用的裝置內容。 您的應用程式競爭為五個一般顯示內容可用在任何指定時間在 Windows 底下。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&42;](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="a-namemhwnda--cclientdcmhwnd"></a><a name="m_hwnd"></a>CClientDC::m_hWnd  
 `HWND`的`CWnd`指標用來建構`CClientDC`物件。  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>備註  
 `m_hWnd`這是受保護的變數。  
  
### <a name="example"></a>範例  
  請參閱範例[CClientDC::CClientDC](#cclientdc)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)

