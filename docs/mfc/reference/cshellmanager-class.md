---
title: "CShellManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
dev_langs: C++
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 550851e383acf988aa9a816ab1d15675da5b54b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cshellmanager-class"></a>CShellManager 類別
實作數個可讓您使用識別項清單指標 (PIDL) 的方法。  
  
## <a name="syntax"></a>語法  
  
```  
class CShellManager : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CShellManager::CShellManager](#cshellmanager)|建構 `CShellManager` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CShellManager::BrowseForFolder](#browseforfolder)|顯示對話方塊，可讓使用者選取 shell 資料夾。|  
|[CShellManager::ConcatenateItem](#concatenateitem)|串連兩個 Pidl。|  
|[CShellManager::CopyItem](#copyitem)|建立新的 PIDL，並將它複製提供的 PIDL。|  
|[CShellManager::CreateItem](#createitem)|建立新的 PIDL 指定的大小。|  
|[CShellManager::FreeItem](#freeitem)|刪除提供的 PIDL。|  
|[CShellManager::GetItemCount](#getitemcount)|提供 PIDL 中傳回的項目數。|  
|[CShellManager::GetItemSize](#getitemsize)|傳回提供 PIDL 大小。|  
|[CShellManager::GetNextItem](#getnextitem)|從 PIDL 傳回下一個項目。|  
|[CShellManager::GetParentItem](#getparentitem)|擷取提供項目的父項目。|  
|[CShellManager::ItemFromPath](#itemfrompath)|擷取所提供的路徑識別項目的 PIDL。|  
  
## <a name="remarks"></a>備註  
 方法的`CShellManager`類別 Pidl 所有處理。 PIDL 是 shell 物件的唯一識別碼。  
  
 您不應建立`CShellManager`手動物件。 它將會自動建立應用程式的架構。 不過，您應該呼叫[CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)的過程中初始化您的應用程式。 若要取得您的應用程式的殼層管理員的指標，呼叫[CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CShellManager](../../mfc/reference/cshellmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxshellmanager.h  
  
##  <a name="browseforfolder"></a>CShellManager::BrowseForFolder  
 顯示對話方塊，可讓使用者選取 shell 資料夾。  
  
```  
BOOL BrowseForFolder(
    CString& strOutFolder,  
    CWnd* pWndParent = NULL,  
    LPCTSTR lplszInitialFolder = NULL,  
    LPCTSTR lpszTitle = NULL,  
    UINT ulFlags = BIF_RETURNONLYFSDIRS,  
    LPINT piFolderImage = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `strOutFolder`  
 字串，此方法用來儲存所選資料夾的路徑。  
  
 [in] `pWndParent`  
 父視窗的指標。  
  
 [in] `lplszInitialFolder`  
 字串，包含 對話方塊顯示時，依預設會選取的資料夾。  
  
 [in] `lpszTitle`  
 對話方塊標題。  
  
 [in] `ulFlags`  
 指定的對話方塊選項旗標。 請參閱[BROWSEINFO](http://msdn.microsoft.com/library/windows/desktop/bb773205)詳細描述。  
  
 [輸出] `piFolderImage`  
 方法寫入所選資料夾的影像索引位置的整數值的指標。  
  
### <a name="return-value"></a>傳回值  
 如果使用者選取資料夾 對話方塊中，從非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 當您呼叫這個方法時，建立應用程式，並顯示對話方塊，可讓使用者選取的資料夾。 方法會寫入至資料夾的路徑`strOutFolder`參數。  
  
### <a name="example"></a>範例  
 下列範例示範如何擷取的參照`CShellManager`物件使用`CWinAppEx::GetShellManager`方法以及如何使用`BrowseForFolder`方法。 此程式碼片段是部分[總管範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]  
  
##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem  
 建立新的清單包含兩個 Pidl。  
  
```  
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,  
    LPCITEMIDLIST pidl2);
```  
  
### <a name="parameters"></a>參數  
 [in] `pidl1`  
 第一個項目中。  
  
 [in] `pidl2`  
 第二個項目中。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，否則為新項目清單的指標`NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法會建立新[ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321)夠大，無法同時包含`pidl1`和`pidl2`。 然後將複製`pidl1`和`pidl2`新清單。  
  
##  <a name="copyitem"></a>CShellManager::CopyItem  
 將複製的項目清單。  
  
```  
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```  
  
### <a name="parameters"></a>參數  
 [in] `pidlSource`  
 原始的項目清單。  
  
### <a name="return-value"></a>傳回值  
 如果成功，新建立的項目清單的指標否則`NULL`。  
  
### <a name="remarks"></a>備註  
 新建立的項目清單會有相同的來源項目清單的大小。  
  
##  <a name="createitem"></a>CShellManager::CreateItem  
 建立新的 PIDL。  
  
```  
LPITEMIDLIST CreateItem(UINT cbSize);
```  
  
### <a name="parameters"></a>參數  
 [in] `cbSize`  
 項目清單的大小。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 建立的項目清單的指標否則`NULL`。  
  
##  <a name="cshellmanager"></a>CShellManager::CShellManager  
 建構 `CShellManager` 物件。  
  
```  
CShellManager();
```  
  
### <a name="remarks"></a>備註  
 在大部分情況下，您不必建立`CShellManager`直接。 根據預設，此架構為您建立一個。 若要取得的指標`CShellManager`，呼叫[CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。 如果您建立`CShellManager`以手動方式，您必須初始化執行個體與方法[CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)。  
  
##  <a name="freeitem"></a>CShellManager::FreeItem  
 刪除項目清單。  
  
```  
void FreeItem(LPITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pidl`  
 若要刪除項目清單。  
  
##  <a name="getitemcount"></a>CShellManager::GetItemCount  
 傳回項目清單中的項目數目。  
  
```  
UINT GetItemCount(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pidl`  
 項目清單的指標。  
  
### <a name="return-value"></a>傳回值  
 項目清單中的項目數目。  
  
##  <a name="getitemsize"></a>CShellManager::GetItemSize  
 傳回項目清單的大小。  
  
```  
UINT GetItemSize(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pidl`  
 項目清單的指標。  
  
### <a name="return-value"></a>傳回值  
 項目清單的大小。  
  
##  <a name="getnextitem"></a>CShellManager::GetNextItem  
 擷取下一個項目從指標 (PIDL) 的項目識別項清單。  
  
```  
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```  
  
### <a name="parameters"></a>參數  
 [in] `pidl`  
 要逐一查看的項目清單。  
  
### <a name="return-value"></a>傳回值  
 在清單中下一個項目指標。  
  
### <a name="remarks"></a>備註  
 如果沒有更多的項目清單中有，則這個方法會傳回`NULL`。  
  
##  <a name="getparentitem"></a>CShellManager::GetParentItem  
 擷取父系的項目識別碼清單 (PIDL) 的指標。  
  
```  
int GetParentItem(
    LPCITEMIDLIST lpidl,  
    LPITEMIDLIST& lpidlParent);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpidl`  
 PIDL，將擷取其父代。  
  
 [輸出] `lpidlParent`  
 方法會在其中儲存結果 PIDL 參考。  
  
### <a name="return-value"></a>傳回值  
 父 PIDL 層級。  
  
### <a name="remarks"></a>備註  
 PIDL 的層級是相對於桌面。 桌面 PIDL 被視為具有等級 0。  
  
##  <a name="itemfrompath"></a>CShellManager::ItemFromPath  
 從字串路徑所識別的項目中擷取項目識別碼清單 (PIDL) 的指標。  
  
```  
HRESULT ItemFromPath(
    LPCTSTR lpszPath,  
    LPITEMIDLIST& pidl);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszPath`  
 字串，指定項目的路徑。  
  
 [輸出] `pidl`  
 PIDL 參考。 方法會使用這個 PIDL 儲存它的傳回值的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回`NOERROR`成功; 如果 OLE 定義的錯誤值。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
