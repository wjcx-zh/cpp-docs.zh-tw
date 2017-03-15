---
title: "CMFCShellListCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellListCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellListCtrl class
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: 30
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
ms.openlocfilehash: 8adac043d30d7555522c05165ffd3856c5999872
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 類別
`CMFCShellListCtrl`類別提供視窗清單控制項功能，並加入擴充包括能夠顯示 shell 項目清單。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|顯示所提供的資料夾中包含的項目清單。|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|顯示是目前顯示資料夾的父資料夾中包含的項目的清單。|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快顯功能表。|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|擷取目前的資料夾路徑。|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|擷取目前的資料夾名稱。|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|傳回目前的清單控制項項目的 PIDL。|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|讓指標回到目前的殼層資料夾中。|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|傳回文字的項目路徑。|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|傳回殼層清單控制項所顯示的項目類型。|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|檢查目前選取的資料夾是否為 [桌面] 資料夾。|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|它會比較兩個項目時，架構會呼叫這個方法。 (覆寫[CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)。)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|架構會擷取清單控制項所顯示的檔案日期時呼叫。|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|架構會將檔案大小的清單控制項時呼叫。|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|架構會擷取圖示清單控制項項目時呼叫。|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|架構將轉換的文字清單控制項項目時呼叫。|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|它會將設定的資料行名稱時，由架構呼叫。|  
|[CMFCShellListCtrl::Refresh](#refresh)|重新整理，並重新繪製該清單控制項。|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|設定顯示在清單控制項項目的型別。|  
  
## <a name="remarks"></a>備註  
 `CMFCShellListCtrl`類別擴充功能的[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)藉由啟用您的程式，列出 Windows 殼層項目。 所使用的顯示格式如下的檔案總管視窗的清單檢視。  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件可以與相關聯`CMFCShellListCtrl`物件來建立完整的 [總管] 視窗。 然後，選取中的項目`CMFCShellTreeCtrl`會導致`CMFCShellListCtrl`列出選取的項目內容的物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立的物件`CMFCShellListCtrl`類別以及如何顯示目前所顯示資料夾的上層資料夾。 此程式碼片段是一部分[總管範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer #&1;](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer #&2;](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer #&3;](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 `CMFCShellListCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxshelllistCtrl.h  
  
##  <a name="a-namedisplayfoldera--cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder  
 顯示所提供的資料夾中包含的項目清單。  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszPath`  
 字串，其中包含資料夾路徑。  
  
 [in] `lpItemInfo`  
 指標`LPAFX_SHELLITEMINFO`描述要顯示的資料夾結構。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，`E_FAIL`否則。  
  
##  <a name="a-namedisplayparentfoldera--cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder  
 更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件，以顯示目前所顯示資料夾的上層資料夾。  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，`E_FAIL`否則。  
  
##  <a name="a-nameenableshellcontextmenua--cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu  
 啟用快顯功能表。  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 布林值，指定架構是否啟用快顯功能表。  
  
##  <a name="a-namegetcurrentfoldera--cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder  
 擷取目前選取的資料夾中的路徑[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strPath`  
 字串參數的方法寫入路徑的位置參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果沒有資料夾中選取`CMFCShellListCtrl`。  
  
##  <a name="a-namegetcurrentfoldernamea--cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName  
 擷取目前選取的資料夾中的名稱[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strName`  
 其中的方法，將名稱寫入字串參數的參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果沒有資料夾中選取`CMFCShellListCtrl`。  
  
##  <a name="a-namegetcurrentitemidlista--cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList  
 傳回目前所選項目的 PIDL。  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前項目的 PIDL。  
  
##  <a name="a-namegetcurrentshellfoldera--cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder  
 取得目前選取的項目中的指標[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[IShellFolder 介面](http://msdn.microsoft.com/library/windows/desktop/bb775075)針對選取的物件。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`NULL`如果目前沒有選取任何物件。  
  
##  <a name="a-namegetitempatha--cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShellListCtrl::GetItemPath  
 擷取項目的路徑。  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strPath`  
 接收路徑字串的參考。  
  
 [in] `iItem`  
 清單項目的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 所提供的索引`iItem`根據目前所顯示的項目[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
##  <a name="a-namegetitemtypesa--cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes  
 傳回所顯示的項目型別[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539)包含列出的項目類型的值`CMFCShellListCtrl`。  
  
### <a name="remarks"></a>備註  
 若要設定列出的項目類型`CMFCShellListCtrl`，呼叫[CMFCShellListCtrl::SetItemTypes](#setitemtypes)。  
  
##  <a name="a-nameisdesktopa--cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop  
 如果資料夾，就是會決定顯示在[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件是 [桌面] 資料夾。  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果顯示的資料夾 [桌面] 資料夾。`FALSE`否則。  
  
##  <a name="a-nameoncompareitemsa--cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>參數  
 [in] `lParam1`  
 [in] `lParam2`  
 [in] `iColumn`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonformatfiledatea--cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate  
 它必須轉換成字串，與物件相關聯的日期時，架構會呼叫這個方法。  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [in] `tmFile`  
 與檔案關聯的日期。  
  
 [輸出] `str`  
 字串，包含格式的檔案的日期。  
  
### <a name="remarks"></a>備註  
 當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件顯示與檔案相關聯的日期，它必須將該日期轉換成字串格式。 `CMFCShellListCtrl`進行該轉換會使用這個方法。 根據預設，此方法會使用目前的地區設定日期格式轉換為字串。  
  
##  <a name="a-nameonformatfilesizea--cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize  
 將物件大小轉換成字串時，架構會呼叫這個方法。  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [in] `lFileSize`  
 架構會顯示檔案的大小。  
  
 [輸出] `str`  
 字串，包含格式的檔案大小。  
  
### <a name="remarks"></a>備註  
 當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件需要顯示檔案的大小，它必須轉換成字串格式的檔案大小。 `CMFCShellListCtrl`進行該轉換會使用這個方法。 根據預設，這個方法會將檔案大小位元組轉換成 kb，並再使用目前的地區設定來格式化成字串的大小。  
  
##  <a name="a-nameongetitemicona--cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon  
 架構會呼叫這個方法來擷取與殼層清單項目相關聯的圖示。  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>參數  
 [in] `iItem`  
 項目索引。  
  
 [in] `pItem`  
 A`LPAFX_SHELLITEMINFO`參數描述項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功，圖示影像的索引在函數失敗時，為-1。  
  
### <a name="remarks"></a>備註  
 圖示的影像索引為基礎的系統映像清單。  
  
 根據預設，這個方法依賴`pItem`參數。 值`iItem`不是預設的實作。 您可以使用`iItem`來實作自訂行為。  
  
##  <a name="a-nameongetitemtexta--cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText  
 必須擷取 shell 項目的文字時，架構會呼叫這個方法。  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>參數  
 [in] `iItem`  
 項目索引。  
  
 [in] `iColumn`  
 感興趣的資料行。  
  
 [in] `pItem`  
 A`LPAFX_SHELLITEMINFO`參數描述項目。  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含與項目相關聯的文字。  
  
### <a name="remarks"></a>備註  
 在每個項目`CMFCShellListCtrl`物件只能有一個或多個資料行中的文字。 架構會呼叫這個方法，它會指定它感興趣的資料行。 如果您以手動方式呼叫此函式，您也必須指定您感興趣的資料行。  
  
 根據預設，這個方法依賴`pItem`參數，來判斷這項程序。 值`iItem`不是預設的實作。  
  
##  <a name="a-nameonsetcolumnsa--cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns  
 它會將設定的資料行名稱時，架構會呼叫這個方法。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>備註  
 根據預設，此架構會建立四個資料行中的`CMFCShellListCtrl`物件。 這些資料行的名稱是`Name`， `Size`， `Type`，和`Modified`。 您可以覆寫這個方法來自訂資料行數目和他們的名稱。  
  
##  <a name="a-namerefresha--cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::Refresh  
 重新整理，並重新繪製[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，否則為錯誤值。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來重新整理所顯示的項目清單`CMFCShellListCtrl`物件。  
  
##  <a name="a-namesetitemtypesa--cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes  
 設定項目中所列的型別[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTypes`  
 清單項目的型別`CMFCShellListCtrl`物件支援。  
  
### <a name="remarks"></a>備註  
 項目類型的清單的相關資訊，請參閱[SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)

