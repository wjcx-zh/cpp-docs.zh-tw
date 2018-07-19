---
title: CCommonDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6821b7a33339b2a143778172caa7a4a22cb101e
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335911"
---
# <a name="ccommondialog-class"></a>CCommonDialog 類別
封裝 Windows 通用對話方塊功能之類別的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|建構 `CCommonDialog` 物件。|  
  
## <a name="remarks"></a>備註  
 下列類別會封裝 Windows 通用對話方塊的功能：  
  
- [CFileDialog](../../mfc/reference/cfiledialog-class.md)  
  
- [CFontDialog](../../mfc/reference/cfontdialog-class.md)  
  
- [CColorDialog](../../mfc/reference/ccolordialog-class.md)  
  
- [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)  
  
- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)  
  
- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)  
  
- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)  
  
- [COleDialog](../../mfc/reference/coledialog-class.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `CCommonDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdlgs.h  
  
##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog  
 建構 `CCommonDialog` 物件。  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>參數  
 *pParentWnd*  
 指向的父系或擁有者的視窗物件 (型別的[CWnd](../../mfc/reference/cwnd-class.md)) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊物件的父視窗設為主要的應用程式視窗。  
  
### <a name="remarks"></a>備註  
 請參閱[CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog)如需完整資訊。  
  
## <a name="see-also"></a>另請參閱  
 [CDialog 類別](../../mfc/reference/cdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)   
 [CFontDialog 類別](../../mfc/reference/cfontdialog-class.md)   
 [CColorDialog 類別](../../mfc/reference/ccolordialog-class.md)   
 [CPageSetupDialog 類別](../../mfc/reference/cpagesetupdialog-class.md)   
 [CPrintDialog 類別](../../mfc/reference/cprintdialog-class.md)   
 [CFindReplaceDialog 類別](../../mfc/reference/cfindreplacedialog-class.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)
