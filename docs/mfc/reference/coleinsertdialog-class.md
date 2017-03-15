---
title: "COleInsertDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleInsertDialog
dev_langs:
- C++
helpviewer_keywords:
- OLE Insert Object dialog box
- dialog boxes, OLE
- COleInsertDialog class
- Insert Object dialog box
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
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
ms.openlocfilehash: 078f421dacc79ff929249cd35c520b0c4d4a222e
ms.lasthandoff: 02/24/2017

---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 類別
用於 OLE 的 [插入物件] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|建構 `COleInsertDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|建立對話方塊中選取的項目。|  
|[COleInsertDialog::DoModal](#domodal)|顯示 OLE 插入物件 對話方塊。|  
|[COleInsertDialog::GetClassID](#getclassid)|取得**CLSID**與所選的項目。|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|會指示是否要繪製圖示的項目。|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示表單相關聯的中繼檔的控制代碼。|  
|[COleInsertDialog::GetPathName](#getpathname)|取得對話方塊中選擇的檔案的完整路徑。|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|取得選取的物件類型。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|型別的結構**OLEUIINSERTOBJECT**控制 對話方塊中的行為。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COleInsertDialog`當您想要呼叫此對話方塊。 之後`COleInsertDialog`在建構物件，您可以使用[m_io](#m_io)結構初始化的值或在對話方塊中控制項的狀態。 `m_io`結構的型別是**OLEUIINSERTOBJECT**。 如需有關如何使用這個對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。  
  
> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。  
  
 如需詳細資訊，請參閱[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需有關特定 OLE 對話方塊的詳細資訊，請參閱文章[OLE 中的對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxodlgs.h  
  
##  <a name="a-namecoleinsertdialoga--coleinsertdialogcoleinsertdialog"></a><a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog  
 此函式建構只`COleInsertDialog`物件。  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 建立旗標，包含任何數目的位元 OR 運算子結合下列值︰  
  
- **IOF_SHOWHELP**指定呼叫對話方塊時，是否會顯示 [說明] 按鈕。  
  
- **IOF_SELECTCREATENEW**指定呼叫對話方塊時，一開始選取 建立新的選項按鈕。 這是預設值，而且不能與**IOF_SELECTCREATEFROMFILE**。  
  
- **IOF_SELECTCREATEFROMFILE**指定呼叫對話方塊時，一開始選取從檔案建立 選項按鈕。 不能與**IOF_SELECTCREATENEW**。  
  
- **IOF_CHECKLINK**指定呼叫對話方塊時，一開始檢查連結核取方塊。  
  
- **IOF_DISABLELINK**指定呼叫對話方塊時，會停用連結核取方塊。  
  
- **IOF_CHECKDISPLAYASICON**指定以圖示顯示核取方塊將會檢查一開始，將會顯示目前的圖示，然後呼叫對話方塊時，將會啟用 [變更圖示] 按鈕。  
  
- **IOF_VERIFYSERVERSEXIST**指定對話方塊中，應該驗證就會加入到清單方塊確保系統註冊資料庫中指定的伺服器有對話方塊顯示之前的類別。 設定這個旗標會明顯降低效能。  
  
 `pParentWnd`  
 會指向父系或擁有者視窗物件 (型別`CWnd`) 對話方塊物件所屬。 如果是**NULL**，主應用程式視窗來設定對話方塊物件的父視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示對話方塊，請呼叫[DoModal](#domodal)函式。  
  
##  <a name="a-namecreateitema--coleinsertdialogcreateitem"></a><a name="createitem"></a>COleInsertDialog::CreateItem  
 呼叫此函式建立型別的物件[COleClientItem](../../mfc/reference/coleclientitem-class.md)才[DoModal](#domodal)傳回**IDOK**。  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 要建立之項目的點。  
  
### <a name="return-value"></a>傳回值  
 建立項目; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 您必須配置`COleClientItem`物件之前，您可以呼叫此函式。  
  
##  <a name="a-namedomodala--coleinsertdialogdomodal"></a><a name="domodal"></a>COleInsertDialog::DoModal  
 呼叫此函式來顯示 OLE 插入物件 對話方塊。  
  
```  
virtual INT_PTR   
    DoModal();

 
INT_PTR   
    DoModal(DWORD  dwFlags);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 下列其中一個值：  
  
 `COleInsertDialog::DocObjectsOnly`插入只 DocObjects。  
  
 `COleInsertDialog::ControlsOnly`插入只有 ActiveX 控制項。  
  
 DocObject 或 ActiveX 控制項都不會插入零。 這個值會產生相同的實作，做為第一個原型上面所列。  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
-   如果已成功地顯示之對話方塊的 ，IDOK。  
  
-   如果使用者已取消對話方塊，IDCANCEL。  
  
-   IDABORT 發生錯誤。 如果傳回 IDABORT，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式，以取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325)函式中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化不同的對話方塊控制項[m_io](#m_io)結構，您應該執行這項操作之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取設定或輸入 [使用者] 對話方塊的資訊。  
  
##  <a name="a-namegetclassida--coleinsertdialoggetclassid"></a><a name="getclassid"></a>COleInsertDialog::GetClassID  
 呼叫此函式可取得**CLSID**與選取的項目只有當相關聯[DoModal](#domodal)傳回**IDOK**和選取項目型別是**COleInsertDialog::createNewItem**。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回**CLSID**與選取的項目相關聯。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetdrawaspecta--coleinsertdialoggetdrawaspect"></a><a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect  
 呼叫此函式可判斷使用者是否選擇選取的項目顯示為圖示。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 此方法需要呈現物件。  
  
- `DVASPECT_CONTENT`傳回以圖示顯示核取方塊未核取。  
  
- `DVASPECT_ICON`傳回以圖示顯示核取方塊已核取。  
  
### <a name="remarks"></a>備註  
 呼叫此函式才[DoModal](#domodal)傳回**IDOK**。  
  
 繪製層面的詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)資料結構中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegeticonicmetafilea--coleinsertdialoggeticonicmetafile"></a><a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile  
 呼叫此函式可取得中繼檔，其中包含選取的項目圖示的層面的控制代碼。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果是以圖示顯示核取方塊，其中包含選取的項目圖示的層面的中繼檔的控制代碼檢查時已藉由選擇關閉對話方塊**確定**，否則為**NULL**。  
  
##  <a name="a-namegetpathnamea--coleinsertdialoggetpathname"></a><a name="getpathname"></a>COleInsertDialog::GetPathName  
 呼叫此函式可取得的完整路徑的所選的檔案才[DoModal](#domodal)傳回**IDOK**和選取項目類型不是**COleInsertDialog::createNewItem**。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在對話方塊中選取的檔案完整路徑。 如果選取項目型別是`createNewItem`，此函數會傳回沒有意義`CString`在發行模式中或在偵錯模式下引起判斷提示。  
  
##  <a name="a-namegetselectiontypea--coleinsertdialoggetselectiontype"></a><a name="getselectiontype"></a>COleInsertDialog::GetSelectionType  
 呼叫此函式可取得選取項目類型，選擇 [插入物件] 對話方塊中選擇時解除**確定**。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 型別所做的選擇。  
  
### <a name="remarks"></a>備註  
 傳回型別值由**選取**中宣告列舉型別`COleInsertDialog`類別。  
  
 `enum Selection`  
  
 `{`  
  
 `createNewItem,`  
  
 `insertFromFile,`  
  
 `linkToFile`  
  
 `};`  
  
 請依照下列這些值的簡短描述︰  
  
- **COleInsertDialog::createNewItem**建立新的選項按鈕已選取。  
  
- **COleInsertDialog::insertFromFile**從檔案建立選項按鈕已選取和未檢查連結核取方塊。  
  
- **COleInsertDialog::linkToFile**已選取 從檔案建立選項按鈕和 連結 核取方塊已勾選。  
  
##  <a name="a-namemioa--coleinsertdialogmio"></a><a name="m_io"></a>COleInsertDialog::m_io  
 型別的結構**OLEUIINSERTOBJECT**可用來控制插入物件 對話方塊的行為。  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)

