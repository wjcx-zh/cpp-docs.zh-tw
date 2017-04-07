---
title: "COleDocObjectItem 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDocObjectItem class
- document object containment
- containment
- containment, doc object
- doc object containment
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 0815454fa4b194e97a2d16a621cfc25da61d5fd0
ms.lasthandoff: 02/24/2017

---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem 類別
實作主動式文件內含項目。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|建構`COleDocObject`項目。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|列印使用預設的印表機設定的容器應用程式的文件。|  
|[COleDocObjectItem::ExecCommand](#execcommand)|執行使用者指定的命令。|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|擷取文件的使用中的檢視。|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|擷取容器應用程式的文件中的頁數。|  
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|容器應用程式的文件準備列印。|  
|[COleDocObjectItem::OnPrint](#onprint)|容器應用程式的文件列印。|  
|[COleDocObjectItem::QueryCommand](#querycommand)|查詢使用者介面事件所產生之一或多個命令的狀態。|  
|[COleDocObjectItem::Release](#release)|釋放連接至 OLE 連結的項目並將它關閉，如果它已開啟。 不會終結的用戶端項目。|  
  
## <a name="remarks"></a>備註  
 在 MFC 中，主動式文件處理同樣的規則、 就地編輯內嵌，具有下列差異︰  
  
-   `COleDocument`-衍生的類別仍然會維護一份目前內嵌的項目; 不過，這些項目可能`COleDocObjectItem`-衍生的項目。  
  
-   使用主動式文件時，會佔用整個工作區的檢視時就地啟用作用中。  
  
-   主動式文件容器擁有完整控制權**協助**功能表。  
  
-   **協助**功能表包含主動式文件容器和伺服器的功能表項目。  
  
 由於主動式文件容器擁有**協助** 功能表中，容器會負責轉送伺服器**協助**功能表訊息到伺服器。 這項整合由`COleDocObjectItem`。  
  
 如需有關功能表合併和主動式文件啟動的詳細資訊，請參閱概觀[作用中的文件內含項目](../../mfc/active-document-containment.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem  
 呼叫此成員函式來初始化`COleDocObjectItem`物件。  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pContainerDoc`  
 指標`COleDocument`做為主動式文件容器的物件。 這個參數必須是**NULL**啟用**IMPLEMENT_SERIALIZE**。 通常將 OLE 項目建構與非**NULL**文件指標。  
  
##  <a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting  
 使用預設設定的文件的架構所呼叫。  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pCaller`  
 指標[CView](../../mfc/reference/cview-class.md)傳送列印命令的物件。  
  
 `pInfo`  
 指標[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件，描述列印工作。  
  
##  <a name="execcommand"></a>COleDocObjectItem::ExecCommand  
 呼叫此成員函式，來執行命令，使用者所指定。  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nCmdID`  
 要執行的命令識別項。 所識別的群組中必須是`pguidCmdGroup`。  
  
 `nCmdExecOpt`  
 指定命令執行選項。 根據預設，設定，才能執行此命令不會提示使用者。 請參閱[OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930)值的清單。  
  
 `pguidCmdGroup`  
 命令群組的唯一識別碼。 根據預設， **NULL**，它會指定標準的群組。 命令傳遞`nCmdID`必須屬於該群組。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`如果成功; 否則傳回下列錯誤碼的其中一個。  
  
|值|說明|  
|-----------|-----------------|  
|**E_UNEXPECTED**|發生意外的錯誤。|  
|**E_FAIL**|發生錯誤。|  
|**E_NOTIMPL**|表示 MFC 本身應該嘗試轉譯和分派命令。|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`為非**NULL** ，但未指定可辨識的命令群組。|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`無法辨識為有效的命令群組 pGroup 中。|  
|**OLECMDERR_DISABLED**|由命令`nCmdID`已停用，無法執行。|  
|**OLECMDERR_NOHELP**|呼叫端所識別的指令上要求協助`nCmdID`但沒有說明。|  
|**OLECMDERR_CANCELLED**|使用者已取消執行。|  
  
### <a name="remarks"></a>備註  
 `pguidCmdGroup`和`nCmdID`參數會共同唯一識別要叫用的命令。 `nCmdExecOpt`參數會指定要採取的確切動作。  
  
##  <a name="getactiveview"></a>COleDocObjectItem::GetActiveView  
 若要取得的指標，此成員函式的呼叫`IOleDocumentView`目前使用中檢視的介面。  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[IOleDocumentView](http://msdn.microsoft.com/library/windows/desktop/ms678455)目前使用中檢視的介面。 如果有任何目前的檢視，則會傳回**NULL**。  
  
### <a name="remarks"></a>備註  
 針對傳回的參考計數`IOleDocumentView`指標這個函式傳回之前不會遞增。  
  
##  <a name="getpagecount"></a>COleDocObjectItem::GetPageCount  
 呼叫此成員函式擷取的文件中的頁數。  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>參數  
 *pnFirstPage*  
 文件的第一頁的數目指標。 可以是**NULL**，表示呼叫端不需要這個數字。  
  
 *pcPages*  
 文件中的頁面總數的指標。 可以是**NULL**，表示呼叫端不需要這個數字。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting  
 準備進行列印的文件架構會呼叫此成員函式。  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pCaller`  
 指標[CView](../../mfc/reference/cview-class.md)傳送列印命令的物件。  
  
 `pInfo`  
 指標[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件，描述列印工作。  
  
 `bPrintAll`  
 指定是否要列印整份文件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="onprint"></a>COleDocObjectItem::OnPrint  
 若要列印的文件架構會呼叫此成員函式。  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pCaller`  
 正在傳送列印命令 CView 物件的指標。  
  
 `pInfo`  
 指標[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)物件，描述列印工作。  
  
 `bPrintAll`  
 指定是否要列印整份文件。  
  
##  <a name="querycommand"></a>COleDocObjectItem::QueryCommand  
 查詢使用者介面事件所產生之一或多個命令的狀態。  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>參數  
 `nCmdID`  
 要查詢的命令識別項。  
  
 `pdwStatus`  
 查詢結果傳回的旗標指標。 如需可能的值，請參閱[OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237)。  
  
 `pCmdText`  
 指標[OLECMDTEXT](http://msdn.microsoft.com/library/windows/desktop/ms693314)結構，以傳回單一命令的名稱和狀態資訊。 可以是**NULL** ，表示呼叫端不需要這項資訊。  
  
 `pguidCmdGroup`  
 命令群組; 的唯一識別碼可以是**NULL**來指定標準的群組。  
  
### <a name="return-value"></a>傳回值  
 傳回值的完整清單，請參閱[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)方法中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="release"></a>COleDocObjectItem::Release  
 釋放連接至 OLE 連結的項目並將它關閉，如果它已開啟。 不會終結的用戶端項目。  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>參數  
 `dwCloseOption`  
 指定要載入的狀態傳回時，OLE 項目儲存在哪些情況之下旗標。 如需可能的值，請參閱[COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close)。  
  
### <a name="remarks"></a>備註  
 不會終結的用戶端項目。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MFCBIND](../../visual-cpp-samples.md)   
 [COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem 類別](../../mfc/reference/cdocobjectserveritem-class.md)

