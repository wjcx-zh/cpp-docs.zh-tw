---
title: "COleCmdUI 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs:
- C++
helpviewer_keywords:
- document object server
- COleCmdUI class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
caps.latest.revision: 21
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
ms.openlocfilehash: 38e7019d7636166262028d955455cee675824f8b
ms.lasthandoff: 02/24/2017

---
# <a name="colecmdui-class"></a>COleCmdUI 類別
實作 MFC 的方法以更新與應用程式 `IOleCommandTarget`驅動功能相關聯之使用者介面物件的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|建構 `COleCmdUI` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|設定或清除 啟用命令旗標。|  
|[COleCmdUI::SetCheck](#setcheck)|設定狀態的開啟/關閉切換命令。|  
|[COleCmdUI::SetText](#settext)|傳回命令的文字名稱或狀態字串。|  
  
## <a name="remarks"></a>備註  
 未啟用 DocObjects，當使用者在應用程式，MFC 處理程序檢視 功能表上的應用程式中**UPDATE_COMMAND_UI**通知。 指定每個通知[CCmdUI](../../mfc/reference/ccmdui-class.md)反映特定命令的狀態可操作的物件。 不過，當您的應用程式啟用 DocObjects，MFC 處理**UPDATE_OLE_COMMAND_UI**通知，並將指派`COleCmdUI`物件。  
  
 `COleCmdUI`允許 DocObject 接收命令來自其容器的使用者介面 （例如 FileNew、 Open、 列印等），並允許容器接收來自 DocObject 的使用者介面的命令。 雖然`IDispatch`無法用來分派相同的命令，`IOleCommandTarget`更簡單的方式來查詢和執行，因為它會依賴一組標準的命令，通常不使用引數，且涉及到任何型別資訊。 `COleCmdUI`可用來啟用、 更新和設定其他屬性的 DocObject 使用者介面的命令。 當您想要叫用該命令時，呼叫[COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。  
  
 如需 DocObjects 詳細資訊，請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。 另請參閱[網際網路第一個步驟︰ 主動式文件](../../mfc/active-documents-on-the-internet.md)和[主動式文件](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdocobj.h  
  
##  <a name="colecmdui"></a>COleCmdUI::COleCmdUI  
 建構`COleCmdUI`與特定的使用者介面命令相關聯的物件。  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>參數  
 `rgCmds`  
 與指定 GUID 相關聯的支援命令清單。 **OLECMD**命令旗標與結構產生關聯的命令。  
  
 *cCmds*  
 中的命令計數`rgCmds`。  
  
 `pGroup`  
 識別一組命令的 GUID 指標。  
  
### <a name="remarks"></a>備註  
 `COleCmdUI`物件提供程式設計介面，以更新 DocObject 使用者介面物件，例如功能表項目或控制列按鈕。 使用者介面物件可以是啟用、 停用、 檢查，和/或透過清除`COleCmdUI`物件。  
  
##  <a name="enable"></a>COleCmdUI::Enable  
 呼叫此函式可設定的命令旗標`COleCmdUI`物件傳遞給**OLECOMDF_ENABLED**，這會告知介面命令是可用且已啟用，或清除命令旗標。  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>參數  
 `bOn`  
 指出是否與命令相關聯`COleCmdUI`物件應該啟用或停用。 Nonzero 啟用命令。0 會停用此命令。  
  
##  <a name="setcheck"></a>COleCmdUI::SetCheck  
 呼叫此函式可設定狀態的開啟/關閉切換命令。  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>參數  
 `nCheck`  
 值，判斷要設定的開啟/關閉切換狀態命令。 值為：  
  
|值|說明|  
|-----------|-----------------|  
|**1**|若要在設定的命令。|  
|**2**|設定的命令，以不確定。無法判斷狀態，因為這個命令的屬性就會採用同時關閉相關的選取範圍中的狀態。|  
|任何其他值|設定為 off 的命令。|  
  
##  <a name="settext"></a>COleCmdUI::SetText  
 呼叫此函式來傳回命令的文字名稱或狀態字串。  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `lpszText`  
 若要命令適用於文字指標。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




