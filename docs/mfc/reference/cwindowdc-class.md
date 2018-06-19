---
title: CWindowDC 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7867f35a66abf0f5a33ecd411b81111e84e3800f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368478"
---
# <a name="cwindowdc-class"></a>CWindowDC 類別
衍生自 `CDC`。  
  
## <a name="syntax"></a>語法  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|建構 `CWindowDC` 物件。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|`HWND`這個`CWindowDC`附加。|  
  
## <a name="remarks"></a>備註  
 呼叫 Windows 函式[GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)在建構階段和[ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx)在解構階段。 這表示`CWindowDC`物件存取整個螢幕區域[CWnd](../../mfc/reference/cwnd-class.md) （用戶端和非工作區）。  
  
 如需有關使用`CWindowDC`，請參閱[裝置內容](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>需求  
 標頭： afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 建構`CWindowDC`物件存取整個螢幕區域 （用戶端和非工作） 的`CWnd`指向的物件`pWnd`。  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>參數  
 `pWnd`  
 視窗裝置內容物件存取其工作區中。  
  
### <a name="remarks"></a>備註  
 建構函式會呼叫 Windows 函式[GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947)。  
  
 例外狀況 (型別`CResourceException`) 則會擲回 Windows`GetWindowDC`呼叫就會失敗。 裝置內容可能無法使用，如果 Windows 已有已配置所有其可用的裝置內容。 您的應用程式競爭的五個一般顯示內容可用在任何指定的時間，在 Windows 下。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 `HWND`的`CWnd`指標用來建構`CWindowDC`物件。  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>備註  
 `m_hWnd` 這是受保護的型別變數`HWND`。  
  
### <a name="example"></a>範例  
  請參閱範例的[CWindowDC::CWindowDC](#cwindowdc)。  
  
## <a name="see-also"></a>另請參閱  
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)
