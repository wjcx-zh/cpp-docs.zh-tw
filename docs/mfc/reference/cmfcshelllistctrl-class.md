---
title: "CMFCShellListCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
dev_langs: C++
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4b5204fe92685431ccdd2c6735553c9b7ce85bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 類別
`CMFCShellListCtrl`類別提供視窗清單控制項功能，並加入顯示 shell 項目清單的能力擴充。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|顯示所提供的資料夾中包含的項目清單。|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|顯示目前所顯示的資料夾的父系資料夾中包含的項目清單。|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|啟用或停用快顯功能表。|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|擷取目前資料夾的路徑。|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|擷取目前的資料夾名稱。|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|傳回目前清單控制項項目的 PIDL。|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|讓指標回到目前的殼層資料夾中。|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|傳回文字的項目路徑。|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|傳回清單控制項所顯示的 Shell 項目類型。|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|檢查目前選取的資料夾是否為 [桌面] 資料夾。|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|架構會呼叫這個方法時，它會比較兩個項目。 (覆寫[CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)。)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|架構會擷取清單控制項所顯示的檔案日期時呼叫。|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|此架構將轉換的檔案大小的清單控制項時呼叫。|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|架構會擷取清單控制項項目的圖示時呼叫。|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|架構會將轉換的清單控制項項目文字時呼叫。|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|它會設定的資料行名稱時由架構呼叫。|  
|[CMFCShellListCtrl::Refresh](#refresh)|重新整理並重新繪製該清單控制項。|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|設定顯示在清單控制項的項目類型。|  
  
## <a name="remarks"></a>備註  
 `CMFCShellListCtrl`類別會擴充功能的[CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)藉由啟用您的程式來列出 Windows shell 項目。 所使用的顯示格式會類似檔案總管視窗的清單檢視。  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)物件可以與相關聯`CMFCShellListCtrl`物件以建立完整的 [總管] 視窗。 然後，選取中的項目`CMFCShellTreeCtrl`會導致`CMFCShellListCtrl`物件來列出選取之項目的內容。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立物件的`CMFCShellListCtrl`類別以及如何顯示目前所顯示的資料夾的上層資料夾。 此程式碼片段是部分[總管範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 `CMFCShellListCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxshelllistCtrl.h  
  
##  <a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder  
 顯示所提供的資料夾中包含的項目清單。  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszPath`  
 字串，包含的資料夾路徑。  
  
 [輸入] `lpItemInfo`  
 指標`LPAFX_SHELLITEMINFO`描述要顯示的資料夾結構。  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，`E_FAIL`否則。  
  
##  <a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder  
 更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件，以顯示目前所顯示的資料夾的上層資料夾。  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，`E_FAIL`否則。  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu  
 啟用快顯功能表。  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 布林值，指定架構是否啟用快顯功能表。  
  
##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder  
 擷取目前選取的資料夾中的路徑[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strPath`  
 字串參數之方法的路徑的寫入位置參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會失敗，如果有任何資料夾中選取`CMFCShellListCtrl`。  
  
##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName  
 擷取中目前選取的資料夾名稱[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strName`  
 字串參數之方法的名稱的寫入位置參考。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會失敗，如果有任何資料夾中選取`CMFCShellListCtrl`。  
  
##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList  
 傳回目前選取之項目的 PIDL。  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的項目 PIDL。  
  
##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder  
 取得目前選取的項目中的指標[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[IShellFolder 介面](http://msdn.microsoft.com/library/windows/desktop/bb775075)針對選取的物件。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回`NULL`如果目前選取的物件。  
  
##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath  
 擷取項目的路徑。  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strPath`  
 接收路徑字串的參考。  
  
 [輸入] `iItem`  
 清單項目的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果登錄成功。，`FALSE`否則。  
  
### <a name="remarks"></a>備註  
 所提供的索引`iItem`根據目前所顯示的項目[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes  
 傳回的類型顯示的項目[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539)包含項目中所列的型別值`CMFCShellListCtrl`。  
  
### <a name="remarks"></a>備註  
 若要設定的項目中所列類型`CMFCShellListCtrl`，呼叫[CMFCShellListCtrl::SetItemTypes](#setitemtypes)。  
  
##  <a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop  
 如果資料夾，就是會決定顯示在[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件是 [桌面] 資料夾。  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果顯示的資料夾 [桌面] 資料夾。`FALSE`否則。  
  
##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lParam1`  
 [輸入] `lParam2`  
 [輸入] `iColumn`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate  
 它必須轉換成字串，與物件相關聯的日期時，架構會呼叫這個方法。  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `tmFile`  
 與檔案關聯的日期。  
  
 [輸出] `str`  
 字串，包含日期的格式的檔案的日期。  
  
### <a name="remarks"></a>備註  
 當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件顯示與檔案相關聯的日期，它必須將該日期轉換成字串格式。 `CMFCShellListCtrl`進行該轉換會使用這個方法。 根據預設，這個方法會使用目前的地區設定來將日期格式化成字串。  
  
##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize  
 物件大小轉換成字串時，架構會呼叫這個方法。  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lFileSize`  
 架構會顯示檔案的大小。  
  
 [輸出] `str`  
 字串，包含格式的檔案大小。  
  
### <a name="remarks"></a>備註  
 當[CMFCShellListCtrl 類別](../../mfc/reference/cmfcshelllistctrl-class.md)物件需要顯示檔案的大小，它必須轉換成字串格式的檔案大小。 `CMFCShellListCtrl`進行該轉換會使用這個方法。 根據預設，此方法會將檔案大小從位元組轉換成 kb 為單位，而且然後會使用目前的地區設定格式化成字串的大小。  
  
##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon  
 架構會呼叫這個方法，以擷取與殼層清單項目相關聯的圖示。  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iItem`  
 項目索引。  
  
 [輸入] `pItem`  
 A`LPAFX_SHELLITEMINFO`參數描述項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 圖示影像的索引如果此函數失敗-1。  
  
### <a name="remarks"></a>備註  
 圖示的影像索引為基礎的系統映像清單。  
  
 根據預設，這個方法依賴`pItem`參數。 值`iItem`不是預設的實作。 您可以使用`iItem`來實作自訂行為。  
  
##  <a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText  
 它必須擷取 shell 項目的文字時，架構會呼叫這個方法。  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iItem`  
 項目索引。  
  
 [輸入] `iColumn`  
 感興趣的資料行。  
  
 [輸入] `pItem`  
 A`LPAFX_SHELLITEMINFO`參數描述項目。  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含與項目相關聯的文字。  
  
### <a name="remarks"></a>備註  
 每個項目`CMFCShellListCtrl`物件可能有一或多個資料行中的文字。 架構會呼叫這個方法，它會指定它感興趣的資料行。 如果您手動呼叫這個函式，您也必須指定您感興趣的資料行。  
  
 根據預設，這個方法依賴`pItem`參數，來判斷其項目至處理序。 值`iItem`不是預設的實作。  
  
##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns  
 它會設定的資料行名稱時，架構會呼叫這個方法。  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>備註  
 根據預設，架構會建立四個資料行`CMFCShellListCtrl`物件。 這些資料行的名稱是`Name`， `Size`， `Type`，和`Modified`。 您可以覆寫這個方法以自訂欄位數目以及它們的名稱。  
  
##  <a name="refresh"></a>CMFCShellListCtrl::Refresh  
 重新整理，並重新繪製[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>傳回值  
 `S_OK`如果登錄成功。，否則錯誤值。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以重新整理顯示的項目清單`CMFCShellListCtrl`物件。  
  
##  <a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes  
 設定項目中所列的型別[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)物件。  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nTypes`  
 項目的清單類型`CMFCShellListCtrl`物件支援。  
  
### <a name="remarks"></a>備註  
 項目類型的清單的相關資訊，請參閱[SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539)。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl 類別](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl 類別](../../mfc/reference/cmfcshelltreectrl-class.md)
