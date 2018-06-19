---
title: CMFCWindowsManagerDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6900164b3ce89031d0db7630c026a302616511c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366560"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 類別
`CMFCWindowsManagerDialog`物件可讓使用者管理 MDI 應用程式中的 MDI 子視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCWindowsManagerDialog : public CDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|建構 `CMFCWindowsManagerDialog` 物件。|  
  
## <a name="remarks"></a>備註  
 `CMFCWindowsManagerDialog`包含應用程式中目前開啟的 MDI 子視窗的清單。 使用者可以使用此對話方塊，手動控制 MDI 子視窗的狀態。  
  
 `CMFCWindowsManagerDialog` 內嵌於[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。 `CMFCWindowsManagerDialog`不是您應該手動建立的類別。 請改為呼叫此函式[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)，並將建立並顯示`CMFCWindowsManagerDialog`物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCWindowsManagerDialog`藉由呼叫物件`CMDIFrameWndEx::ShowWindowsDialog`。 此程式碼片段是部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxWindowsManagerDialog.h  
  
##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog  
 建構[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)物件。  
  
```  
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,  
    BOOL bHelpButton = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pMDIFrame`  
 父系或擁有者視窗的指標。  
  
 [輸入] `bHelpButton`  
 布林值參數，指定是否要顯示架構**協助** 按鈕。  
  
### <a name="remarks"></a>備註  
 如需視覺管理員的詳細資訊，請參閱[視覺化管理員](../../mfc/visualization-manager.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)
