---
title: "COleDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
dev_langs: C++
helpviewer_keywords: COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae60b9e5a0d2e79d2bf6d9cc06eebfa9df0c6e23
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="coledialog-class"></a>COleDialog 類別
提供 OLE 對話方塊通用的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDialog : public CCommonDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleDialog::GetLastError](#getlasterror)|取得對話方塊所傳回的錯誤碼。|  
  
## <a name="remarks"></a>備註  
 Microsoft Foundation 類別庫會提供數個類別衍生自`COleDialog`:  
  
- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)  
  
- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)  
  
- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)  
  
- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)  
  
- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)  
  
- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)  
  
- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)  
  
- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)  
  
 如需 OLE 特定對話方塊的詳細資訊，請參閱文章[中 OLE 對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `COleDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxodlgs.h  
  
##  <a name="getlasterror"></a>COleDialog::GetLastError  
 呼叫`GetLastError`成員函式來取得其他錯誤資訊時`DoModal`傳回**IDABORT**。  
  
```  
UINT GetLastError() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所傳回的錯誤碼`GetLastError`取決於特定顯示的對話方塊。  
  
### <a name="remarks"></a>備註  
 請參閱`DoModal`特定的錯誤訊息的相關資訊的衍生類別中的成員函式。  
  
## <a name="see-also"></a>請參閱  
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



