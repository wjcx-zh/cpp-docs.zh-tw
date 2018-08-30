---
title: COleConvertDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c63eda0bbe734bd7c9f0a972e6756a444369123
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212426"
---
# <a name="coleconvertdialog-class"></a>COleConvertDialog 類別
如需詳細資訊，請參閱 < [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) Windows SDK 中的結構。  
  
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
|[COleConvertDialog::DoConvert](#doconvert)|執行在對話方塊中指定的轉換。|  
|[COleConvertDialog::DoModal](#domodal)|會顯示 OLE 變更項目 對話方塊。|  
|[COleConvertDialog::GetClassID](#getclassid)|取得所選的項目相關聯的 CLSID。|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|指定是否要繪製項目做為圖示。|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示格式相關聯的中繼檔的控制代碼。|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|取得選取範圍選擇的型別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|結構，以控制對話方塊的行為。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  應用程式精靈所產生的容器程式碼會使用這個類別。  
  
 如需有關特定 OLE 對話方塊的詳細資訊，請參閱[對話方塊，在 OLE 中](../../mfc/dialog-boxes-in-ole.md)。  
  
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
  
##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog  
 只會建構`COleConvertDialog`物件。  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 *pItem*  
 指向要轉換或啟動的項目。  
  
 *dwFlags*  
 建立旗標，其中包含任意數目的下列值可讓您結合使用位元的 or 運算子：  
  
- CF_SELECTCONVERTTO 指定要轉換為選項按鈕選取一開始時呼叫對話方塊。 這是預設值。  
  
- CF_SELECTACTIVATEAS 指定要啟用做為選項按鈕選取一開始時呼叫的對話方塊。  
  
- CF_SETCONVERTDEFAULT 指定的類別所指定的 CLSID`clsidConvertDefault`隸屬`m_cv`結構將會用為預設選項類別清單方塊中，選取 轉換為選項按鈕時。  
  
- CF_SETACTIVATEDEFAULT 指定的類別所指定的 CLSID`clsidActivateDefault`隸屬`m_cv`結構將會用作為預設選項類別清單方塊中，選取 啟用做為選項按鈕時。  
  
- CF_SHOWHELPBUTTON 指定對話方塊中呼叫時，會顯示 [說明] 按鈕。  
  
 *pClassID*  
 指向 CLSID 的轉換或啟動的項目。 如果是 NULL，與相關聯的 CLSID *pItem*將使用。  
  
 *pParentWnd*  
 指向的父系或擁有者的視窗物件 (類型的`CWnd`) 所屬之對話方塊物件。 如果它是 NULL 時，對話方塊中的父視窗設為主要的應用程式視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。  
  
 如需詳細資訊，請參閱 < [CLSID 金鑰](/windows/desktop/com/clsid-key-hklm)並[OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta)結構。  
  
##  <a name="doconvert"></a>  COleConvertDialog::DoConvert  
 呼叫此函式，傳回已成功從之後[DoModal](#domodal)可以轉換，或是在啟動型別的物件[COleClientItem](../../mfc/reference/coleclientitem-class.md)。  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 *pItem*  
 指向要轉換或啟動的項目。 不可以是 NULL。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 轉換或啟動根據使用者在 [轉換] 對話方塊中選取的資訊項目。  
  
##  <a name="domodal"></a>  COleConvertDialog::DoModal  
 呼叫此函式可顯示 OLE 轉換 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- 如果對話方塊已成功顯示，IDOK。  
  
- 如果使用者已取消對話方塊，IDCANCEL。  
  
- IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱 < [OleUIConvert](/windows/desktop/api/oledlg/nf-oledlg-oleuiconverta) Windows SDK 中的函式。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種不同的對話方塊控制項[m_cv](#m_cv)結構，您應該執行這項操作之前先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取 [設定] 或 [已由使用者輸入] 對話方塊中的資訊。  
  
##  <a name="getclassid"></a>  COleConvertDialog::GetClassID  
 呼叫此函式可取得 CLSID 項目相關聯轉換對話方塊中選取的使用者。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 轉換對話方塊中選取的項目相關聯的 CLSID。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後，才[DoModal](#domodal)傳回 IDOK。  
  
 如需詳細資訊，請參閱 < [CLSID 金鑰](/windows/desktop/com/clsid-key-hklm)Windows SDK 中。  
  
##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect  
 呼叫此函式可判斷使用者是否選擇要選取的項目顯示為圖示。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 需要來呈現物件的方法。  
  
- 如果未檢查以圖示顯示核取方塊，就會傳回 DVASPECT_CONTENT。  
  
- 如果已核取圖示以顯示核取方塊，就會傳回 DVASPECT_ICON。  
  
### <a name="remarks"></a>備註  
 呼叫此函式之後，才[DoModal](#domodal)傳回 IDOK。  
  
 如需有關繪圖外觀的詳細資訊，請參閱[FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Windows SDK 中的資料結構。  
  
##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile  
 呼叫此函式可取得包含選取的項目圖示的層面之中繼檔的控制代碼。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含選取的項目圖示的層面，以圖示顯示核取方塊時的中繼檔的控制代碼可讓您檢查時已選擇 [確定]，關閉對話方塊否則為 NULL。  
  
##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType  
 呼叫此函式可判斷轉換對話方塊中選取轉換類型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所做的選取項目的類型。  
  
### <a name="remarks"></a>備註  
 所指定的傳回型別值`Selection`列舉型別中宣告`COleConvertDialog`類別。  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 請依照下列這些值的簡短描述：  
  
- `COleConvertDialog::noConversion` 如果已取消 [] 對話方塊中，或使用者選取的任何轉換傳回。 如果`COleConvertDialog::DoModal`傳回 IDOK，就可以選取不同的圖示，比先前選取的使用者。  
  
- `COleConvertDialog::convertItem` 傳回轉換為選項按鈕核取方塊，如果使用者選取要轉換成，另一個項目和`DoModal`傳回 IDOK。  
  
- `COleConvertDialog::activateAs` 傳回啟用為選項按鈕核取方塊，如果使用者選取不同的項目，若要啟用，和`DoModal`傳回 IDOK。  
  
##  <a name="m_cv"></a>  COleConvertDialog::m_cv  
 類型 OLEUICONVERT 結構用來控制轉換對話方塊的行為。  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>備註  
 直接或透過成員函式，則可以修改此結構的成員。  
  
 如需詳細資訊，請參閱 < [OLEUICONVERT](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiconverta) Windows SDK 中的結構。  
  
## <a name="see-also"></a>另請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)
