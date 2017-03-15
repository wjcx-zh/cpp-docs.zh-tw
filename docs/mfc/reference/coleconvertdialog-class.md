---
title: "COleConvertDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleConvertDialog
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog class
- OLE Convert dialog box
- dialog boxes, OLE
- OLE dialog boxes, Convert
- Convert dialog box
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 6db5caf443e7f71c58e2c65b46794c2c9d246d38
ms.lasthandoff: 02/24/2017

---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 類別
如需詳細資訊，請參閱[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|建構 `COleConvertDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|執行在對話方塊中指定的轉換。|  
|[COleConvertDialog::DoModal](#domodal)|顯示 OLE 變更項目 對話方塊。|  
|[COleConvertDialog::GetClassID](#getclassid)|取得**CLSID**與所選的項目。|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否要繪製項目以圖示。|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示表單相關聯的中繼檔的控制代碼。|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|取得選擇型別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|控制行為 對話方塊中的結構。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。  
  
 如需 OLE 特定對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="a-namecoleconvertdialoga--coleconvertdialogcoleconvertdialog"></a><a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
 只有建構`COleConvertDialog`物件。  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指向要轉換或啟動的項目。  
  
 `dwFlags`  
 建立旗標，其中包含下列值的任何數字結合使用位元的 or 運算子︰  
  
- **CF_SELECTCONVERTTO**指定呼叫對話方塊時，一開始選取轉換為選項按鈕。 這是預設值。  
  
- **CF_SELECTACTIVATEAS**指定呼叫對話方塊時，一開始選取為 [啟動] 選項按鈕。  
  
- **CF_SETCONVERTDEFAULT**指定類別的**CLSID**所指定**clsidConvertDefault**成員`m_cv`轉換為選項按鈕已選取時，將成為預設選項類別清單方塊中使用結構。  
  
- **CF_SETACTIVATEDEFAULT**指定類別的**CLSID**所指定**clsidActivateDefault**成員`m_cv`啟動做為選項按鈕已選取時，將成為預設選項類別清單方塊中使用結構。  
  
- **CF_SHOWHELPBUTTON**指定呼叫對話方塊時，是否會顯示 [說明] 按鈕。  
  
 `pClassID`  
 要轉換或啟動的項目的 CLSID 指標。 如果**NULL**、 **CLSID**聯`pItem`並用。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，對話方塊中的父視窗設定為主要應用程式視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。  
  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)和[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)結構。  
  
##  <a name="a-namedoconverta--coleconvertdialogdoconvert"></a><a name="doconvert"></a>COleConvertDialog::DoConvert  
 呼叫此函式，從成功傳回之後[DoModal](#domodal)，轉換，或是啟動型別的物件[COleClientItem](../../mfc/reference/coleclientitem-class.md)。  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指向要轉換或啟動的項目。 不能是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 轉換或啟動根據使用者在 [轉換] 對話方塊中選取的資訊項目。  
  
##  <a name="a-namedomodala--coleconvertdialogdomodal"></a><a name="domodal"></a>COleConvertDialog::DoModal  
 呼叫此函式來顯示 OLE 轉換 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消的對話方塊。  
  
- **IDABORT**發生錯誤。 如果**IDABORT**會傳回，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化不同的對話方塊控制項[m_cv](#m_cv)結構，您應該執行這項操作之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回**IDOK**，您可以呼叫其他成員函式來擷取設定或已由使用者輸入 對話方塊中的資訊。  
  
##  <a name="a-namegetclassida--coleconvertdialoggetclassid"></a><a name="getclassid"></a>COleConvertDialog::GetClassID  
 呼叫此函式可取得**CLSID**轉換 對話方塊中選取的使用者相關聯的項目。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **CLSID**轉換 對話方塊中所選取的項目相關聯。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式後，才[DoModal](#domodal)傳回**IDOK**。  
  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdrawaspecta--coleconvertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 呼叫此函式可判斷是否在使用者選擇選取的項目顯示為圖示。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此方法需要呈現物件。  
  
- `DVASPECT_CONTENT`傳回以圖示顯示核取方塊未核取。  
  
- `DVASPECT_ICON`傳回以圖示顯示核取方塊已核取。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式後，才[DoModal](#domodal)傳回**IDOK**。  
  
 繪製層面的詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)資料結構中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegeticonicmetafilea--coleconvertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 呼叫此函式可取得中繼檔，其中包含選取的項目圖示的層面的控制代碼。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是以圖示顯示核取方塊，其中包含選取的項目圖示的層面的中繼檔的控制代碼檢查時已藉由選擇關閉對話方塊**確定**，否則為**NULL**。  
  
##  <a name="a-namegetselectiontypea--coleconvertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 呼叫此函式可判斷在 [轉換] 對話方塊中選取轉換類型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 型別所做的選擇。  
  
### <a name="remarks"></a>備註  
 傳回型別值由**選取**中宣告列舉型別`COleConvertDialog`類別。  
  
 `enum Selection`  
  
 `{`  
  
 `noConversion,`  
  
 `convertItem,`  
  
 `activateAs`  
  
 `};`  
  
 請依照下列這些值的簡短描述︰  
  
- **COleConvertDialog::noConversion**傳回如果對話方塊已取消或使用者選取的任何轉換。 如果`COleConvertDialog::DoModal`傳回**IDOK**，就可以選取不同的圖示，比先前選取的使用者。  
  
- **COleConvertDialog::convertItem**傳回使用者如果已核取 轉換為選項按鈕，選取要轉換成，另一個項目和`DoModal`傳回**IDOK**。  
  
- **COleConvertDialog::activateAs**傳回做為啟動選項按鈕已選取，如果使用者選取不同的項目，若要啟用，並`DoModal`傳回**IDOK**。  
  
##  <a name="a-namemcva--coleconvertdialogmcv"></a><a name="m_cv"></a>COleConvertDialog::m_cv  
 型別的結構**OLEUICONVERT**用來控制轉換 對話方塊的行為。  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)

