---
title: "COleLinksDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs:
- C++
helpviewer_keywords:
- Edit Links dialog box
- COleLinksDialog class
- dialog boxes, OLE
- OLE Edit Links dialog box
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ed256b3a4d3236863e3dcccb7614949f650f058b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="colelinksdialog-class"></a>COleLinksDialog 類別
用於 OLE 的 [編輯連結] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|建構 `COleLinksDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](#domodal)|顯示 OLE [編輯連結] 對話方塊。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|型別的結構**OLEUIEDITLINKS**控制 對話方塊中的行為。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COleLinksDialog`當您想要呼叫此對話方塊。 之後`COleLinksDialog`在建構物件，您可以使用[m_el](#m_el)結構初始化的值或在對話方塊中控制項的狀態。 `m_el`結構的型別是**OLEUIEDITLINKS**。 如需有關如何使用這個對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。  
  
> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。  
  
 如需詳細資訊，請參閱[OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="domodal"></a>COleLinksDialog::DoModal  
 顯示 OLE [編輯連結] 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消的對話方塊。  
  
- **IDABORT**發生錯誤。 如果**IDABORT**會傳回，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化不同的對話方塊控制項[m_el](#m_el)結構，應該在執行之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog  
 建構 `COleLinksDialog` 物件。  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDoc`  
 OLE 文件，其中包含要編輯連結的指標。  
  
 `pView`  
 指向目前的檢視上`pDoc`。  
  
 `dwFlags`  
 建立旗標，其中包含 0 或**ELF_SHOWHELP**來指定顯示對話方塊時，是否會顯示 [說明] 按鈕。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，對話方塊中的父視窗設定為主要應用程式視窗。  
  
### <a name="remarks"></a>備註  
 此函式建構只`COleLinksDialog`物件。 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。  
  
##  <a name="m_el"></a>COleLinksDialog::m_el  
 型別的結構**OLEUIEDITLINKS**用來控制行為的編輯連結 對話方塊。  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)

