---
title: CClientDC 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: add135c353366ed54a24c63fcce2101c49d24fe7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338577"
---
# <a name="cclientdc-class"></a>CClientDC 類別
呼叫 Windows 函式會負責[GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)在建構階段並[ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920)在解構階段。  
  
## <a name="syntax"></a>語法  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|建構`CClientDC`物件連接到`CWnd`。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|這個視窗的 HWND`CClientDC`有效。|  
  
## <a name="remarks"></a>備註  
 這表示，與相關聯的裝置內容`CClientDC`物件是視窗工作區。  
  
 如需詳細資訊`CClientDC`，請參閱 <<c2> [ 裝置內容](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cclientdc"></a>  CClientDC::CClientDC  
 建構`CClientDC`存取的工作區的物件[CWnd](../../mfc/reference/cwnd-class.md)所指*pWnd*。  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 *pWnd*  
 視窗的裝置內容物件將會存取其工作區中。  
  
### <a name="remarks"></a>備註  
 建構函式會呼叫 Windows 函式[GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871)。  
  
 例外狀況 (型別的`CResourceException`) 便會擲回 Windows`GetDC`呼叫就會失敗。 裝置內容可能無法使用，如果 Windows 已有配置所有其可用的裝置內容。 您的應用程式競爭五個一般顯示的可用內容，在 Windows 下一次。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CClientDC::m_hWnd  
 `HWND`的`CWnd`指標，用來建構`CClientDC`物件。  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>備註  
 *m_hWnd*是受保護的變數。  
  
### <a name="example"></a>範例  
  範例，請參閱[CClientDC::CClientDC](#cclientdc)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)
