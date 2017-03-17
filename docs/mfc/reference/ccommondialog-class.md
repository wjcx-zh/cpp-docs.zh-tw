---
title: "CCommonDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], Windows common dialogs
- common dialog boxes [C++], common dialog classes
- common dialog classes [C++]
- MFC dialog boxes, Windows common dialogs
- Windows common dialogs [C++]
- CCommonDialog class
- dialog classes [C++], common
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
caps.latest.revision: 20
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
ms.openlocfilehash: 93d4cd4ca794095c225641bc67353b9a53080c3c
ms.lasthandoff: 02/24/2017

---
# <a name="ccommondialog-class"></a>CCommonDialog 類別
封裝 Windows 通用對話方塊功能之類別的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CCommonDialog : public CDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CCommonDialog::CCommonDialog](#ccommondialog)|建構 `CCommonDialog` 物件。|  
  
## <a name="remarks"></a>備註  
 下列類別會封裝 Windows 通用對話方塊的功能︰  
  
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
 **標頭︰** afxdlgs.h  
  
##  <a name="ccommondialog"></a>CCommonDialog::CCommonDialog  
 建構 `CCommonDialog` 物件。  
  
```  
explicit CCommonDialog(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>參數  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別[CWnd](../../mfc/reference/cwnd-class.md)) 對話方塊物件所屬。 如果是**NULL**，對話方塊物件的父視窗設為主要應用程式視窗。  
  
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

