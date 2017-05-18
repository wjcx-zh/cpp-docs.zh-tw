---
title: "COleChangeIconDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs:
- C++
helpviewer_keywords:
- OLE dialog boxes, Change Icon
- OLE Change Icon dialog box
- dialog boxes, OLE
- COleChangeIconDialog class
- Change Icon dialog box
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 07dfd7995bbbdb0f52f55dceedc318d8d702111b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog 類別
用於 OLE 的 [變更圖示] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|建構 `COleChangeIconDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|執行在對話方塊中指定的變更。|  
|[COleChangeIconDialog::DoModal](#domodal)|顯示 OLE 2 變更圖示 對話方塊。|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示表單相關聯的中繼檔的控制代碼。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|控制行為 對話方塊中的結構。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COleChangeIconDialog`當您想要呼叫此對話方塊。 之後`COleChangeIconDialog`在建構物件，您可以使用[m_ci](#m_ci)結構初始化的值或在對話方塊中控制項的狀態。 `m_ci`結構的型別是**OLEUICHANGEICON**。 如需有關如何使用這個對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。  
  
 如需詳細資訊，請參閱[OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需 OLE 特定對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog  
 此函式建構只`COleChangeIconDialog`物件。  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 要轉換之項目的點。  
  
 `dwFlags`  
 建立旗標，其中包含下列值的任何數字結合使用位元的 or 運算子︰  
  
- **CIF_SELECTCURRENT**指定呼叫對話方塊時，一開始選取目前的選項按鈕。 這是預設值。  
  
- **CIF_SELECTDEFAULT**指定呼叫對話方塊時，一開始選取預設選項按鈕。  
  
- **CIF_SELECTFROMFILE**指定呼叫對話方塊時，一開始選取的檔案中的選項按鈕。  
  
- **CIF_SHOWHELP**指定呼叫對話方塊時，是否會顯示 [說明] 按鈕。  
  
- **CIF_USEICONEXE**指定圖示應取自可執行檔中指定**szIconExe**欄位[m_ci](#m_ci)而不是擷取自型別。 這是用於內嵌或連結到非 OLE 檔案。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，對話方塊中的父視窗將會設定為主要應用程式視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。  
  
 如需詳細資訊，請參閱[OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon  
 呼叫此函式來變更表示的項目之後的對話方塊中選取一個圖示[DoModal](#domodal)傳回**IDOK**。  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指向其圖示會變更的項目。  
  
### <a name="return-value"></a>傳回值  
 如果變更成功則為非零否則為 0。  
  
##  <a name="domodal"></a>COleChangeIconDialog::DoModal  
 呼叫此函式來顯示 OLE 的 [變更圖示] 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消的對話方塊。  
  
- **IDABORT**發生錯誤。 如果**IDABORT**會傳回，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIChangeIcon](http://msdn.microsoft.com/library/windows/desktop/ms688307)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化不同的對話方塊控制項[m_ci](#m_ci)結構，您應該執行這項操作之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回**IDOK**，您可以呼叫其他成員函式來擷取設定或已由使用者輸入 對話方塊中的資訊。  
  
##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile  
 呼叫此函式可取得中繼檔，其中包含選取的項目圖示的層面的控制代碼。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果已關閉對話方塊，選擇包含 [新增] 圖示，圖示層面的中繼檔的控制代碼**確定**; 否則對話方塊顯示之前做為它的圖示。  
  
##  <a name="m_ci"></a>COleChangeIconDialog::m_ci  
 型別的結構**OLEUICHANGEICON**可用來控制變更圖示 對話方塊的行為。  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)

