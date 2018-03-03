---
title: "COleConvertDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f93c17416c81d4c152608f4d8a8b78f48e5422c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 類別
如需詳細資訊，請參閱[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) Windows SDK 中的結構。  
  
## <a name="syntax"></a>語法  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|建構 `COleConvertDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|會執行在對話方塊中指定的轉換。|  
|[COleConvertDialog::DoModal](#domodal)|顯示 OLE 變更項目 對話方塊。|  
|[COleConvertDialog::GetClassID](#getclassid)|取得**CLSID**與所選的項目相關聯。|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否要繪製項目為圖示。|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示表單相關聯的中繼檔的控制代碼。|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|取得選擇的型別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|結構，控制對話方塊中的行為。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。  
  
 如需 OLE 特定對話方塊的詳細資訊，請參閱文章[中 OLE 對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxodlgs.h  
  
##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
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
 指向要啟用或轉換的項目。  
  
 `dwFlags`  
 使用位元結合起來建立旗標，其中包含下列值的任何數字-or 運算子：  
  
- **CF_SELECTCONVERTTO**指定對話方塊中呼叫時，一開始選取轉換為選項按鈕。 這是預設值。  
  
- **CF_SELECTACTIVATEAS**指定對話方塊中呼叫時，一開始選取做為啟動選項按鈕。  
  
- **CF_SETCONVERTDEFAULT**指定類別其**CLSID**所指定**clsidConvertDefault**隸屬`m_cv`結構做為預設值當轉換為選項按鈕的類別清單方塊中選取項目為已選取。  
  
- **CF_SETACTIVATEDEFAULT**指定類別其**CLSID**所指定**clsidActivateDefault**隸屬`m_cv`結構做為預設值在類別清單方塊中選取 啟用做為選項按鈕時的選取範圍。  
  
- **CF_SHOWHELPBUTTON**指定呼叫對話方塊時，會顯示 [說明] 按鈕。  
  
 `pClassID`  
 指向 CLSID 要啟用或轉換的項目。 如果**NULL**、 **CLSID**聯`pItem`將使用。  
  
 `pParentWnd`  
 指向的父系或擁有者的視窗物件 (型別`CWnd`) 所屬之對話方塊物件。 如果是**NULL**，父視窗，在對話方塊的 設定主應用程式視窗為。  
  
### <a name="remarks"></a>備註  
 若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。  
  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)和[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657)結構。  
  
##  <a name="doconvert"></a>COleConvertDialog::DoConvert  
 呼叫此函式，從成功傳回之後[DoModal](#domodal)，要轉換，或啟動型別的物件[COleClientItem](../../mfc/reference/coleclientitem-class.md)。  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指向要啟用或轉換的項目。 不能**NULL**。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 轉換或啟動根據使用者在 [轉換] 對話方塊中選取的資訊項目。  
  
##  <a name="domodal"></a>COleConvertDialog::DoModal  
 呼叫此函式可顯示 OLE 轉換 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消對話方塊。  
  
- **IDABORT**如果發生錯誤。 如果**IDABORT**是傳回，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式來取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) Windows SDK 中的函式。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種對話方塊控制項[m_cv](#m_cv)結構，您應該這麼做會在呼叫之前`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回**IDOK**，您可以呼叫其他成員函式來擷取的設定或已由使用者輸入，在對話方塊中的資訊。  
  
##  <a name="getclassid"></a>COleConvertDialog::GetClassID  
 呼叫此函式可取得**CLSID**轉換 對話方塊中選取的使用者相關聯的項目。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 **CLSID**轉換 對話方塊中選取的項目相關聯。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式之後，才[DoModal](#domodal)傳回**IDOK**。  
  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 呼叫此函式可判斷使用者是否選擇選取的項目顯示為圖示。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 需要來呈現物件的方法。  
  
- `DVASPECT_CONTENT`傳回以圖示顯示核取方塊未核取。  
  
- `DVASPECT_ICON`傳回以圖示顯示核取方塊已核取。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式之後，才[DoModal](#domodal)傳回**IDOK**。  
  
 如需有關繪圖外觀的詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的資料結構。  
  
##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 呼叫此函式可取得包含選取之項目的圖示的外觀的中繼檔的控制代碼。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含所選項目的圖示的外觀，如果是以圖示顯示核取方塊的中繼檔的控制代碼可讓您檢查時已選擇關閉對話方塊**確定**，否則為**NULL**。  
  
##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 呼叫此函式可判斷轉換 對話方塊中選取轉換類型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所做的選取項目的類型。  
  
### <a name="remarks"></a>備註  
 所指定的傳回型別值**選取**列舉類型中宣告`COleConvertDialog`類別。  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 請遵循這些值的簡短說明：  
  
- **COleConvertDialog::noConversion**傳回如果對話方塊已取消或使用者選取的任何轉換。 如果`COleConvertDialog::DoModal`傳回**IDOK**，便可選取不同的圖示，比先前選取的使用者。  
  
- **COleConvertDialog::convertItem**傳回使用者如果已核取 轉換為選項按鈕，選取要轉換成，另一個項目和`DoModal`傳回**IDOK**。  
  
- **COleConvertDialog::activateAs**傳回使用者如果已核取 啟用做為選項按鈕，選取不同的項目，若要啟用，並`DoModal`傳回**IDOK**。  
  
##  <a name="m_cv"></a>COleConvertDialog::m_cv  
 型別的結構**OLEUICONVERT**用來控制轉換 對話方塊的行為。  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) Windows SDK 中的結構。  
  
## <a name="see-also"></a>請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)
