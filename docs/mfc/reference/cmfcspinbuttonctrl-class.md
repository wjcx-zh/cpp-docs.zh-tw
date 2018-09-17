---
title: CMFCSpinButtonCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 960a1a0338a3390fdc10cf03ddc235bcf4ecbae9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712747"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 類別
`CMFCSpinButtonCtrl`類別支援繪製微調按鈕控制項的視覺管理員。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCSpinButtonCtrl : public CSpinButtonCtrl  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|預設建構函式。|  
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|會重新繪製目前的微調按鈕控制項。|  
  
## <a name="remarks"></a>備註  
 若要使用的視覺管理員在您的應用程式中繪製微調按鈕控制項，取代的所有執行個體`CSpinButtonCtrl`類別搭配`CMFCSpinButtonCtrl`類別。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立的物件`CMFCSpinButtonCtrl`類別，並且使用其`Create`方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)  
  
 [CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxspinbuttonctrl.h  
  
##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw  
 會重新繪製目前的微調按鈕控制項。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
*pDC*<br/>
[in]裝置內容指標。  
  
### <a name="remarks"></a>備註  
 這個架構會呼叫`CMFCSpinButtonCtrl::OnPaint`方法以處理[CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint)訊息，且該方法會呼叫這`CMFCSpinButtonCtrl::OnDraw`方法。 覆寫這個方法，以自訂架構繪製微調按鈕控制項的方式。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 類別](../../mfc/reference/cmfcvisualmanager-class.md)
