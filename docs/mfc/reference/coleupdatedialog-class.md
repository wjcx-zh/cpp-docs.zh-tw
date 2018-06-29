---
title: COleUpdateDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0208a24b69c1884d72c0ae525ce95b3d3258271
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079970"
---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 類別
用於 OLE [編輯連結] 對話方塊的特殊狀況，當您只需要更新文件中現有的連結或內嵌物件時，應該使用此項。  
  
## <a name="syntax"></a>語法  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|建構 `COleUpdateDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|顯示**編輯連結**處於更新模式 對話方塊。|  
  
## <a name="remarks"></a>備註  
 如需有關 OLE 特定對話方塊的詳細資訊，請參閱文章[中 OLE 對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxodlgs.h  
  
##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog  
 建構 `COleUpdateDialog` 物件。  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pDoc*  
 指向此文件包含可能需要更新的連結。  
  
 *bUpdateLinks*  
 連結的物件會決定要更新的旗標。  
  
 *bUpdateEmbeddings*  
 內嵌的物件會決定要更新的旗標。  
  
 *pParentWnd*  
 指向的父系或擁有者的視窗物件 (型別`CWnd`) 所屬之對話方塊物件。 如果是**NULL**，對話方塊中的父視窗將會設定為主要的應用程式視窗。  
  
### <a name="remarks"></a>備註  
 此函式會建構只`COleUpdateDialog`物件。 若要顯示的對話方塊，請呼叫[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 應該使用這個類別，而不是`COleLinksDialog`當您想要更新只現有連結或內嵌項目。  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 顯示的 [編輯連結] 對話方塊中，更新模式。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功傳回。  
  
- **IDCANCEL**如果沒有任何連結或內嵌的項目目前的文件中需要更新。  
  
- **IDABORT**如果發生錯誤。 如果**IDABORT**是傳回，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式來取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) Windows SDK 中的函式。  
  
### <a name="remarks"></a>備註  
 除非使用者選取 [取消] 按鈕就會更新所有的連結和/或內嵌。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)
