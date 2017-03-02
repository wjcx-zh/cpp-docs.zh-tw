---
title: "COleUpdateDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleUpdateDialog
dev_langs:
- C++
helpviewer_keywords:
- Update dialog
- links [C++], updating
- updating OLE links
- OLE dialog boxes, Edit Link
- OLE link updating
- COleUpdateDialog class
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
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
ms.openlocfilehash: 8066a8dc9e572c14e9423af62d340e249351ac11
ms.lasthandoff: 02/24/2017

---
# <a name="coleupdatedialog-class"></a>COleUpdateDialog 類別
用於 OLE [編輯連結] 對話方塊的特殊狀況，當您只需要更新文件中現有的連結或內嵌物件時，應該使用此項。  
  
## <a name="syntax"></a>語法  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|建構 `COleUpdateDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|顯示**編輯連結** 對話方塊中更新模式。|  
  
## <a name="remarks"></a>備註  
 如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
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
 **標頭︰** afxodlgs.h  
  
##  <a name="a-namecoleupdatedialoga--coleupdatedialogcoleupdatedialog"></a><a name="coleupdatedialog"></a>COleUpdateDialog::COleUpdateDialog  
 建構 `COleUpdateDialog` 物件。  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDoc`  
 指向包含的連結，可能需要更新的文件。  
  
 *bUpdateLinks*  
 旗標來判斷是否要更新連結的物件。  
  
 *bUpdateEmbeddings*  
 內嵌的物件會決定要更新的旗標。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，對話方塊中的父視窗將會設定為主要應用程式視窗。  
  
### <a name="remarks"></a>備註  
 此函式建構只`COleUpdateDialog`物件。 若要顯示對話方塊，請呼叫[DoModal](../../mfc/reference/colelinksdialog-class.md#domodal)。 應該使用這個類別，而不是`COleLinksDialog`當您想要更新只有現有連結或內嵌項目。  
  
##  <a name="a-namedomodala--coleupdatedialogdomodal"></a><a name="domodal"></a>COleUpdateDialog::DoModal  
 顯示 [編輯連結] 對話方塊中更新模式。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功傳回。  
  
- **IDCANCEL**如果目前的文件中連結或內嵌項目都不需要更新。  
  
- **IDABORT**發生錯誤。 如果**IDABORT**會傳回，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 除非使用者選取 [取消] 按鈕，會更新所有連結和/或內嵌。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleLinksDialog 類別](../../mfc/reference/colelinksdialog-class.md)

