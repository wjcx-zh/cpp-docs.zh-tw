---
title: "COlePasteSpecialDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs:
- C++
helpviewer_keywords:
- Paste Special dialog box
- dialog boxes, Paste Special
- OLE Paste Special dialog box
- COlePasteSpecialDialog class
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 24
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
ms.openlocfilehash: 6984d714248815b062c564c7eed5c315990855af
ms.lasthandoff: 02/24/2017

---
# <a name="colepastespecialdialog-class"></a>COlePasteSpecialDialog 類別
用於 OLE 的 [選擇性貼上] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|建構 `COlePasteSpecialDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|新增自訂格式的格式貼上您的應用程式清單。|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|將新的項目加入至支援的剪貼簿格式的清單。|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|新增**CF_BITMAP**， **CF_DIB**， `CF_METAFILEPICT`，並選擇性地`CF_LINKSOURCE`格式的清單可以貼上您的應用程式。|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|使用指定的格式在容器文件中建立項目。|  
|[COlePasteSpecialDialog::DoModal](#domodal)|顯示 OLE 的 [選擇性貼上] 對話方塊。|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|會指示是否要繪製項目以圖示或不。|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示表單相關聯的中繼檔的控制代碼。|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|取得使用者已選擇使用貼上選項的索引。|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|取得選擇型別。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|型別的結構**OLEUIPASTESPECIAL**控制 對話方塊中的函式。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COlePasteSpecialDialog`當您想要呼叫此對話方塊。 之後`COlePasteSpecialDialog`在建構物件，您可以使用[AddFormat](#addformat)和[AddStandardFormats](#addstandardformats)將剪貼簿格式加入至對話方塊中的成員函式。 您也可以使用[m_ps](#m_ps)結構初始化的值或在對話方塊中控制項的狀態。 `m_ps`結構的型別是**OLEUIPASTESPECIAL**。  
  
 如需詳細資訊，請參閱[OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat  
 呼叫此函式的應用程式可支援選擇性貼上作業中的格式清單中加入新的格式。  
  
```  
void AddFormat(
    const FORMATETC& formatEtc,  
    LPTSTR lpszFormat,  
    LPTSTR lpszResult,  
    DWORD flags);

 
void AddFormat(
    UINT cf,  
    DWORD tymed,  
    UINT nFormatID,  
    BOOL bEnableIcon,  
    BOOL bLink);
```  
  
### <a name="parameters"></a>參數  
 *fmt*  
 要加入的資料類型的參考。  
  
 `lpszFormat`  
 描述使用者格式的字串。  
  
 *lpszResult*  
 描述結果，如果在對話方塊中選擇這種格式的字串。  
  
 `flags`  
 其他連結和內嵌格式選項。 這個旗標是一或多個中的不同值的位元組合**OLEUIPASTEFLAG**列舉型別。  
  
 `cf`  
 要加入的剪貼簿格式。  
  
 *tymed*  
 在這種格式中可用的媒體類型。 這是一或多個值的位元組合**TYMED**列舉型別。  
  
 `nFormatID`  
 識別這個格式的字串識別碼。 此字串的格式是以 '\n' 字元分隔的兩個個別字串。 第一個字串會相同，會傳入*lpstrFormat*參數，而第二個是相同*lpstrResult*參數。  
  
 *bEnableIcon*  
 旗標來判斷是否要在清單方塊中選擇這種格式時，啟用以圖示顯示核取方塊。  
  
 *閃爍*  
 旗標來判斷是否要在清單方塊中選擇這種格式時，啟用 [貼上連結] 選項按鈕。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可以將其中一個標準的格式，例如**CF_TEXT**或**CF_TIFF**或系統已註冊您的應用程式的自訂格式。 如需將資料物件貼到您的應用程式的詳細資訊，請參閱文章[資料物件和資料來源︰ 管理](../../mfc/data-objects-and-data-sources-manipulation.md)。  
  
 如需詳細資訊，請參閱[TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227)列舉型別和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)列舉型別中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry  
 將新的項目加入至支援的剪貼簿格式的清單。  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>參數  
 `cf`  
 要加入的剪貼簿格式。  
  
### <a name="return-value"></a>傳回值  
 [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)結構包含新的連結項目的資訊。  
  
##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats  
 呼叫此函式的應用程式可支援選擇性貼上作業中的格式清單中加入下列的剪貼簿格式︰  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bEnableLink*  
 旗標來判斷是否要加入`CF_LINKSOURCE`格式的清單可以貼上您的應用程式。  
  
### <a name="remarks"></a>備註  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **「 內嵌的物件 」**  
  
-   （選擇性）**「 連結來源 」**  
  
 這些格式用來支援內嵌和連結。  
  
##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog  
 建構 `COlePasteSpecialDialog` 物件。  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 建立旗標，會包含任何數目的下列旗標位元 OR 運算子結合在一起︰  
  
- `PSF_SELECTPASTE`指定呼叫對話方塊時，一開始檢查貼上選項按鈕。 不能搭配`PSF_SELECTPASTELINK`。 這是預設值。  
  
- `PSF_SELECTPASTELINK`指定貼上連結 選項按鈕將會檢查一開始時呼叫 對話方塊。 不能搭配`PSF_SELECTPASTE`。  
  
- `PSF_CHECKDISPLAYASICON`指定呼叫對話方塊時，一開始檢查以圖示顯示核取方塊。  
  
- `PSF_SHOWHELP`指定呼叫對話方塊時，將顯示 [說明] 按鈕。  
  
 `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)貼上文字。 如果這個值是**NULL**，它會取得`COleDataObject`從剪貼簿。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，對話方塊中的父視窗設定為主要應用程式視窗。  
  
### <a name="remarks"></a>備註  
 此函式只建構`COlePasteSpecialDialog`物件。 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。  
  
 如需詳細資訊，請參閱[OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172)列舉型別中的[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="createitem"></a>COlePasteSpecialDialog::CreateItem  
 建立新的項目，選擇 [選擇性貼上] 對話方塊。  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>參數  
 *pNewItem*  
 指向`COleClientItem`執行個體。 不能是**NULL**。  
  
### <a name="return-value"></a>傳回值  
 非零，如果項目建立可順利啟動。否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式應該只呼叫之後[DoModal](#domodal)傳回**IDOK**。  
  
##  <a name="domodal"></a>COlePasteSpecialDialog::DoModal  
 顯示 OLE 的 [選擇性貼上] 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消的對話方塊。  
  
- **IDABORT**發生錯誤。 如果**IDABORT**會傳回，呼叫`COleDialog::GetLastError`成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化不同的對話方塊控制項[m_ps](#m_ps)結構，您應該執行這項操作之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回**IDOK**，您可以呼叫其他成員函式來擷取設定或使用者的資訊輸入到對話方塊。  
  
##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect  
 決定使用者選擇選取的項目顯示為圖示。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此方法需要呈現物件。  
  
- `DVASPECT_CONTENT`傳回已關閉對話方塊時，如果不檢查以圖示顯示核取方塊。  
  
- `DVASPECT_ICON`傳回已關閉對話方塊時，如果選取以圖示顯示核取方塊。  
  
### <a name="remarks"></a>備註  
 只會呼叫此函式之後[DoModal](#domodal)傳回**IDOK**。  
  
 繪製層面的詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile  
 取得使用者所選取的項目相關聯的中繼檔。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含選取的項目圖示的層面，如果選擇 [解除] 對話方塊中選取以圖示顯示核取方塊的中繼檔的控制代碼**確定**，否則為**NULL**。  
  
##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex  
 取得索引值相關聯的項目選取的使用者。  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 陣列的索引**OLEUIPASTEENTRY**使用者所選取的結構。 執行貼上作業時，應對應至選取之索引的格式。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType  
 決定使用者所做的選取項目類型。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回類型所做的選擇。  
  
### <a name="remarks"></a>備註  
 傳回型別值由**選取**中宣告列舉型別`COlePasteSpecialDialog`類別。  
  
 `enum Selection`  
  
 `{`  
  
 `pasteLink,`  
  
 `pasteNormal,`  
  
 `pasteOther,`  
  
 `pasteStatic`  
  
 `};`  
  
 請依照下列這些值的簡短 desccriptions:  
  
- **COlePasteSpecialDialog::pasteLink**已核取貼上連結 選項按鈕和所選擇的格式是標準的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteNormal**貼上選項按鈕已核取和所選擇的格式是標準的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteOther**所選的格式並不是標準的 OLE 格式。  
  
- **COlePasteSpecialDialog::pasteStatic**所選擇的格式是中繼檔。  
  
##  <a name="m_ps"></a>COlePasteSpecialDialog::m_ps  
 型別的結構**OLEUIPASTESPECIAL**用來控制 [選擇性貼上] 對話方塊中的行為。  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)

