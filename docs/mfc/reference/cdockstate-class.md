---
title: "CDockState 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
dev_langs:
- C++
helpviewer_keywords:
- dock state
- size
- docking control bars
- CDockState class
- states, dockable control bar
- position, control bar
- size, control bar
- docking tool windows
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fc8beb80cc35c1816fbc305ece2bfbc5df2e7cd0
ms.lasthandoff: 02/24/2017

---
# <a name="cdockstate-class"></a>CDockState 類別
序列化的 `CObject` 類別，這個類別會在持續性記憶體 (檔案) 中載入、卸載或清除一個或多個停駐控制列的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|清除停駐狀態資訊。|  
|[CDockState::GetVersion](#getversion)|擷取已儲存的版本號碼列狀態。|  
|[CDockState::LoadState](#loadstate)|擷取狀態資訊從登錄或。INI 檔案。|  
|[CDockState::SaveState](#savestate)|將狀態資訊儲存至登錄或 INI 檔案。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|陣列的指標儲存停駐狀態資訊的每一種控制列的一個項目。|  
  
## <a name="remarks"></a>備註  
 停駐狀態包含大小和位置的列和停駐。 當擷取預存停駐狀態，`CDockState`檢查的列位置，如果無法以目前的畫面設定顯示列`CDockState`縮放列的位置，讓它會顯示。 主要目的`CDockState`是保存的控制列的數字的整個狀態，並允許該狀態儲存和載入至登錄，應用程式的。INI 檔案，或以二進位格式的一部分`CArchive`物件的內容。  
  
 列可以是任何可停駐控制列，包括工具列、 狀態列上或對話方塊列。 `CDockState`物件會寫入和讀取或經由`CArchive`物件。  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)擷取狀態資訊的所有框架視窗的`CControlBar`物件，並放入`CDockState`物件。 然後，您可以撰寫的內容`CDockState`物件來搭配儲存體[序列化](../../mfc/reference/cobject-class.md#serialize)或[CDockState::SaveState](#savestate)。 如果您稍後想要還原的框架視窗的控制列的狀態，您可以載入狀態與`Serialize`或[CDockState::LoadState](#loadstate)，然後使用[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)来套用至框架視窗的控制列的 儲存的狀態。  
  
 如需有關如何停駐控制列的詳細資訊，請參閱文章[控制列](../../mfc/control-bars.md)，[工具列︰ 停駐和浮動](../../mfc/docking-and-floating-toolbars.md)，和[框架視窗](../../mfc/frame-windows.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxadv.h  
  
##  <a name="clear"></a>CDockState::Clear  
 呼叫此函式來清除所有停駐的資訊儲存在`CDockState`物件。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>備註  
 這包括不只是否列停駐，但是狀態列的大小和位置，以及它可見。  
  
##  <a name="getversion"></a>CDockState::GetVersion  
 呼叫此函式可擷取已儲存的版本號碼列狀態。  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>傳回值  
 1，否則預存的列資訊是早於目前列檢視狀態。2 如果預存的列資訊是與目前的列的狀態。  
  
### <a name="remarks"></a>備註  
 版本支援啟用修訂過的列，將新的持續性屬性，但也可以偵測並載入所列的是舊版建立的持續性狀態。  
  
##  <a name="loadstate"></a>CDockState::LoadState  
 呼叫此函式可從登錄擷取狀態資訊或。INI 檔案。  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>參數  
 `lpszProfileName`  
 指向以 null teminated 字串，指定的初始設定檔案或儲存狀態資訊的 Windows 登錄中的索引鍵中區段的名稱。  
  
### <a name="remarks"></a>備註  
 設定檔名稱是應用程式的區段。INI 檔案或登錄中包含的資料列的狀態資訊。 您可以將控制列狀態資訊儲存至登錄或。INI 檔案`SaveState`。  
  
##  <a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo  
 A`CPtrArray`物件的每個已儲存狀態資訊的控制列的預存的控制列資訊的指標陣列`CDockState`物件。  
  
```  
CPtrArray m_arrBarInfo;  
```  
  
##  <a name="savestate"></a>CDockState::SaveState  
 呼叫此函式可將狀態資訊儲存至登錄或。INI 檔案。  
  
```  
void SaveState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>參數  
 `lpszProfileName`  
 指向以 null teminated 字串，指定的初始設定檔案或儲存狀態資訊的 Windows 登錄中的索引鍵中區段的名稱。  
  
### <a name="remarks"></a>備註  
 設定檔名稱是應用程式的區段。INI 檔案或登錄，其中包含控制列的狀態資訊。 `SaveState`也會儲存目前的螢幕大小。 您可以從登錄擷取控制列資訊或。INI 檔案`LoadState`。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


