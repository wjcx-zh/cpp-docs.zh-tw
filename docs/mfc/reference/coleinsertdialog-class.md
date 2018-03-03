---
title: "COleInsertDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleInsertDialog
- AFXODLGS/COleInsertDialog
- AFXODLGS/COleInsertDialog::COleInsertDialog
- AFXODLGS/COleInsertDialog::CreateItem
- AFXODLGS/COleInsertDialog::DoModal
- AFXODLGS/COleInsertDialog::GetClassID
- AFXODLGS/COleInsertDialog::GetDrawAspect
- AFXODLGS/COleInsertDialog::GetIconicMetafile
- AFXODLGS/COleInsertDialog::GetPathName
- AFXODLGS/COleInsertDialog::GetSelectionType
- AFXODLGS/COleInsertDialog::m_io
dev_langs:
- C++
helpviewer_keywords:
- COleInsertDialog [MFC], COleInsertDialog
- COleInsertDialog [MFC], CreateItem
- COleInsertDialog [MFC], DoModal
- COleInsertDialog [MFC], GetClassID
- COleInsertDialog [MFC], GetDrawAspect
- COleInsertDialog [MFC], GetIconicMetafile
- COleInsertDialog [MFC], GetPathName
- COleInsertDialog [MFC], GetSelectionType
- COleInsertDialog [MFC], m_io
ms.assetid: a9ec610b-abde-431e-bd01-c40159a66dbb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4638471ed199d08bb21bcf16465fe933af3a584c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="coleinsertdialog-class"></a>COleInsertDialog 類別
用於 OLE 的 [插入物件] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COleInsertDialog : public COleDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleInsertDialog::COleInsertDialog](#coleinsertdialog)|建構 `COleInsertDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleInsertDialog::CreateItem](#createitem)|建立在對話方塊中選取的項目。|  
|[COleInsertDialog::DoModal](#domodal)|顯示 OLE 插入物件 對話方塊。|  
|[COleInsertDialog::GetClassID](#getclassid)|取得**CLSID**與所選的項目相關聯。|  
|[COleInsertDialog::GetDrawAspect](#getdrawaspect)|指示是否要繪製成圖示的項目。|  
|[COleInsertDialog::GetIconicMetafile](#geticonicmetafile)|取得與這個項目的圖示表單相關聯的中繼檔的控制代碼。|  
|[COleInsertDialog::GetPathName](#getpathname)|取得在對話方塊中選擇的檔案的完整路徑。|  
|[COleInsertDialog::GetSelectionType](#getselectiontype)|取得選取的物件類型。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleInsertDialog::m_io](#m_io)|型別的結構**OLEUIINSERTOBJECT**控制對話方塊的行為。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COleInsertDialog`當您想要呼叫此對話方塊。 之後`COleInsertDialog`在建構物件，您可以使用[m_io](#m_io)結構初始化的值或在對話方塊中控制項的狀態。 `m_io`結構的類型是**OLEUIINSERTOBJECT**。 如需有關如何使用這個對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。  
  
> [!NOTE]
>  應用程式精靈產生的容器程式碼會使用這個類別。  
  
 如需詳細資訊，請參閱[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) Windows SDK 中的結構。  
  
 如需有關 OLE 特定對話方塊的詳細資訊，請參閱文章[中 OLE 對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleInsertDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxodlgs.h  
  
##  <a name="coleinsertdialog"></a>COleInsertDialog::COleInsertDialog  
 此函式會建構只`COleInsertDialog`物件。  
  
```  
COleInsertDialog (
    DWORD dwFlags = IOF_SELECTCREATENEW,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `dwFlags`  
 包含任何數目的下列值來使用位元 OR 運算子加以結合，建立旗標：  
  
- **IOF_SHOWHELP**指定呼叫對話方塊時，會顯示 [說明] 按鈕。  
  
- **IOF_SELECTCREATENEW**指定對話方塊中呼叫時，一開始選取建立新的選項按鈕。 這是預設值，而且不能與**IOF_SELECTCREATEFROMFILE**。  
  
- **IOF_SELECTCREATEFROMFILE**指定對話方塊中呼叫時，一開始選取從檔案建立選項按鈕。 不能與**IOF_SELECTCREATENEW**。  
  
- **IOF_CHECKLINK**指定對話方塊中呼叫時，一開始檢查連結核取方塊。  
  
- **IOF_DISABLELINK**指定對話方塊中呼叫時將會停用連結核取方塊。  
  
- **IOF_CHECKDISPLAYASICON**指定一開始要檢查以圖示顯示核取方塊，將會顯示目前的圖示，並呼叫對話方塊時，將會啟用 [變更圖示] 按鈕。  
  
- **IOF_VERIFYSERVERSEXIST**指定對話方塊應會驗證就會加入至清單方塊確保系統註冊資料庫中指定的伺服器有對話方塊顯示之前的類別。 設定這個旗標可能會大幅降低效能。  
  
 `pParentWnd`  
 指向的父系或擁有者的視窗物件 (型別`CWnd`) 所屬之對話方塊物件。 如果是**NULL**，對話方塊物件的父視窗設定為主要的應用程式視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。  
  
##  <a name="createitem"></a>COleInsertDialog::CreateItem  
 呼叫此函式來建立物件的型別[COleClientItem](../../mfc/reference/coleclientitem-class.md)才[DoModal](#domodal)傳回**IDOK**。  
  
```  
BOOL CreateItem(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 要建立之項目的點。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果項目建立;否則便是 0。  
  
### <a name="remarks"></a>備註  
 您必須配置`COleClientItem`物件之前，您可以呼叫此函式。  
  
##  <a name="domodal"></a>COleInsertDialog::DoModal  
 呼叫此函式可顯示 OLE 的 [插入物件] 對話方塊。  
  
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
  
 零插入 DocObject 都 ActiveX 控制項。 這個值會產生相同的實作，做為第一個原型上面所列。  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
-   如果對話方塊已成功顯示，IDOK。  
  
-   如果使用者已取消對話方塊，IDCANCEL。  
  
-   IDABORT 如果發生錯誤。 如果傳回 IDABORT，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式來取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIInsertObject](http://msdn.microsoft.com/library/windows/desktop/ms694325) Windows SDK 中的函式。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種對話方塊控制項[m_io](#m_io)結構，您應該這麼做會在呼叫之前`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回 IDOK，您可以呼叫其他成員函式來擷取設定或在對話方塊中，使用者的資訊輸入。  
  
##  <a name="getclassid"></a>COleInsertDialog::GetClassID  
 呼叫此函式可取得**CLSID**與選取的項目只有當相關聯[DoModal](#domodal)傳回**IDOK**和選取範圍型別是**COleInsertDialog::createNewItem**。  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回**CLSID**與選取的項目相關聯。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[CLSID 金鑰](http://msdn.microsoft.com/library/windows/desktop/ms691424)Windows SDK 中。  
  
##  <a name="getdrawaspect"></a>COleInsertDialog::GetDrawAspect  
 呼叫此函式可判斷使用者是否選擇選取的項目顯示為圖示。  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 需要來呈現物件的方法。  
  
- `DVASPECT_CONTENT`傳回以圖示顯示核取方塊未核取。  
  
- `DVASPECT_ICON`傳回以圖示顯示核取方塊已核取。  
  
### <a name="remarks"></a>備註  
 呼叫此函式才[DoModal](#domodal)傳回**IDOK**。  
  
 如需有關繪圖外觀的詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中的資料結構。  
  
##  <a name="geticonicmetafile"></a>COleInsertDialog::GetIconicMetafile  
 呼叫此函式可取得包含選取之項目的圖示的外觀的中繼檔的控制代碼。  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含所選項目的圖示的外觀，如果是以圖示顯示核取方塊的中繼檔的控制代碼可讓您檢查時已選擇關閉對話方塊**確定**，否則為**NULL**。  
  
##  <a name="getpathname"></a>COleInsertDialog::GetPathName  
 呼叫此函式可取得的完整路徑的 選取的檔案才[DoModal](#domodal)傳回**IDOK**和選取項目類型不是**COleInsertDialog::createNewItem**。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在對話方塊中選取的檔案完整路徑。 如果選取項目類型是`createNewItem`，此函數會傳回無意義`CString`在發行模式中或在偵錯模式下引起判斷提示。  
  
##  <a name="getselectiontype"></a>COleInsertDialog::GetSelectionType  
 呼叫此函式可取得選取項目類型選擇 [插入物件] 對話方塊時選擇解除**確定**。  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所做的選取項目的類型。  
  
### <a name="remarks"></a>備註  
 所指定的傳回型別值**選取**列舉類型中宣告`COleInsertDialog`類別。  
  
```  
enum Selection {
    createNewItem,
    insertFromFile,
    linkToFile
    };  
```  
  
 請遵循這些值的簡短說明：  
  
- **COleInsertDialog::createNewItem**選取建立新的選項按鈕。  
  
- **COleInsertDialog::insertFromFile**已選取 從檔案建立選項按鈕和未檢查連結核取方塊。  
  
- **COleInsertDialog::linkToFile**已選取 從檔案建立選項按鈕和 連結 核取方塊已核取。  
  
##  <a name="m_io"></a>COleInsertDialog::m_io  
 型別的結構**OLEUIINSERTOBJECT**用來控制插入的物件 對話方塊的行為。  
  
```  
OLEUIINSERTOBJECT m_io;  
```  
  
### <a name="remarks"></a>備註  
 您可以修改此結構的成員，直接或透過成員函式。  
  
 如需詳細資訊，請參閱[OLEUIINSERTOBJECT](http://msdn.microsoft.com/library/windows/desktop/ms691316) Windows SDK 中的結構。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)
