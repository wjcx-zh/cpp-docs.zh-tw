---
title: "CRecentFileList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
dev_langs:
- C++
helpviewer_keywords:
- files [C++], most recently used
- MRU files
- CRecentFileList class
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
caps.latest.revision: 19
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
ms.openlocfilehash: 5d18daee2e4d809c750ae4654d731888df1db39e
ms.lasthandoff: 02/24/2017

---
# <a name="crecentfilelist-class"></a>CRecentFileList 類別
支援最近使用的 (MRU) 檔案清單控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CRecentFileList  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CRecentFileList::CRecentFileList](#crecentfilelist)|建構 `CRecentFileList` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRecentFileList::Add](#add)|將檔案加入至最近一次使用的檔案清單。|  
|[CRecentFileList::GetDisplayName](#getdisplayname)|提供功能表顯示的最近一次使用檔案名稱的顯示名稱。|  
|[CRecentFileList::GetSize](#getsize)|擷取最近一次使用檔案清單中的檔案數目。|  
|[CRecentFileList::ReadList](#readlist)|從登錄讀取最近一次使用檔案清單或。INI 檔案。|  
|[CRecentFileList::Remove](#remove)|從最近一次使用檔案清單中移除檔案。|  
|[CRecentFileList::UpdateMenu](#updatemenu)|更新功能表顯示的最近一次使用檔案清單。|  
|[CRecentFileList::WriteList](#writelist)|從登錄中寫入最近一次使用檔案清單或。INI 檔案。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CRecentFileList::operator]](#operator_at)|傳回`CString`物件的指定位置。|  
  
## <a name="remarks"></a>備註  
 可以加入或從最近一次使用檔案清單中刪除檔案、 可讀取或寫入登錄的檔案清單或。您可以更新 INI 檔案，並顯示最近一次使用檔案清單的功能表。  
  
 如需最近一次使用功能表項目，請參閱  
  
-   知識庫文件 Q243751︰ 如何︰ 將 MFC 應用程式中的最近一次使用功能表項目的命令處理常式  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CRecentFileList`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxadv.h  
  
##  <a name="add"></a>CRecentFileList::Add  
 將檔案加入至最近使用過 (MRU) 檔案清單。  
  
```  
virtual void Add(LPCTSTR lpszPathName);

 
virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

 
void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

 
void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

 
void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 指定要加入至清單的路徑名稱。  
  
 `lpszAppID`  
 指定的應用程式的應用程式使用者的模型識別碼。  
  
 `pItem`  
 指定要加入至清單的殼層項目的指標。  
  
 `pLink`  
 指定要加入至清單的 Shell 連結的指標。  
  
 `pidl`  
 指定應該將最新的文件資料夾的殼層項目的 IDLIST。  
  
### <a name="remarks"></a>備註  
 檔案名稱會新增至 MRU 清單頂端。 如果 MRU 清單中的檔案名稱已經存在，便會移至最上方。  
  
##  <a name="crecentfilelist"></a>CRecentFileList::CRecentFileList  
 建構 `CRecentFileList` 物件。  
  
```  
CRecentFileList(
    UINT nStart,  
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntryFormat,  
    int nSize,  
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```  
  
### <a name="parameters"></a>參數  
 `nStart`  
 在功能表上顯示的 MRU （最近使用的） 檔案清單編號的位移。  
  
 `lpszSection`  
 登錄或應用程式的部分的名稱指標。其中最近一次使用檔案清單會讀取與/或寫入的 INI 檔案。  
  
 `lpszEntryFormat`  
 指向用於儲存在登錄或應用程式的項目名稱的格式字串。INI 檔案。  
  
 `nSize`  
 最近一次使用檔案清單中的檔案數目上限。  
  
 `nMaxDispLen`  
 最大長度，以字元為單位，可供功能表顯示的最近一次使用檔案清單中的檔名。  
  
### <a name="remarks"></a>備註  
 格式字串所指`lpszEntryFormat`應該包含"%d"，用於取代每個最近一次使用項目的索引。 例如，如果格式字串是`"file%d"`項目將會命名為`file0`， `file1`，依此類推。  
  
##  <a name="getdisplayname"></a>CRecentFileList::GetDisplayName  
 取得在最近一次使用檔案清單中，檔案以供使用，在功能表上顯示的 MRU 清單的顯示名稱。  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>參數  
 `strName`  
 要顯示在最近一次使用檔案功能表清單中的檔案名稱的完整路徑。  
  
 `nIndex`  
 最近一次使用檔案清單中的檔案的以零為起始的索引。  
  
 *lpszCurDir*  
 保存目前的目錄的字串。  
  
 *nCurDir*  
 目前的目錄字串的長度。  
  
 `bAtLeastName`  
 如果是非零值，指出，應該會傳回檔案的基底名稱，即使它已超過最大可顯示長度 (以傳遞`nMaxDispLen`參數`CRecentFileList`建構函式)。  
  
### <a name="return-value"></a>傳回值  
 **FALSE**有沒有任何檔案名稱的指定索引處最近使用過 (MRU) 檔案清單。  
  
### <a name="remarks"></a>備註  
 如果檔案是在目前的目錄中，函式會使隱藏目錄。 如果檔案名稱太長，則會予以去除目錄和延伸模組。 如果仍然太長檔名，顯示名稱設為空字串除非`bAtLeastName`為非零值。  
  
##  <a name="getsize"></a>CRecentFileList::GetSize  
 擷取最近一次使用檔案清單中的檔案數目。  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在目前的檔案數目最近使用 (過 MRU) 檔案清單。  
  
##  <a name="operator_at"></a>CRecentFileList::operator]  
 多載的註標 ( `[]`) 運算子會傳回單一`CString`中以零為起始的索引所指定`nIndex`。  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 以零為起始的索引`CString`集中的`CString`s。  
  
##  <a name="readlist"></a>CRecentFileList::ReadList  
 讀取最近使用過的 (MRU) 檔案清單，從登錄或應用程式。INI 檔案。  
  
```  
virtual void ReadList();
```  
  
##  <a name="remove"></a>CRecentFileList::Remove  
 從最近一次使用檔案清單中移除檔案。  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 要從最近使用過 (MRU) 檔案清單中移除之檔案的以零為起始的索引。  
  
##  <a name="updatemenu"></a>CRecentFileList::UpdateMenu  
 更新功能表顯示的最近一次使用檔案清單。  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>參數  
 `pCmdUI`  
 指標[CCmdUI](../../mfc/reference/ccmdui-class.md)最近使用過 (MRU) 檔案清單 功能表中的物件。  
  
##  <a name="writelist"></a>CRecentFileList::WriteList  
 寫入到登錄或應用程式的最最近使用過的 (MRU) 檔案清單。INI 檔案。  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)




