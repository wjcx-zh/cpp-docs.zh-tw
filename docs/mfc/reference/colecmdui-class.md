---
title: COleCmdUI 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
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
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ece2d45bdce490d09c7195deec380728d79392d
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535226"
---
# <a name="colecmdui-class"></a>COleCmdUI 類別
實作 MFC 的方法以更新與應用程式 `IOleCommandTarget`驅動功能相關聯之使用者介面物件的狀態。  
  
## <a name="syntax"></a>語法  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|建構 `COleCmdUI` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|設定或清除 啟用命令旗標。|  
|[COleCmdUI::SetCheck](#setcheck)|設定開啟/關閉切換狀態命令。|  
|[COleCmdUI::SetText](#settext)|傳回命令的文字名稱或狀態字串。|  
  
## <a name="remarks"></a>備註  
 應用程式中，未啟用 DocObjects，當使用者檢視的功能表中應用程式時，MFC 處理 UPDATE_COMMAND_UI 便。 指定每個通知[CCmdUI](../../mfc/reference/ccmdui-class.md)以反映特定命令的狀態可操作的物件。 不過，當 DocObjects 啟用您的應用程式時，MFC 處理 UPDATE_OLE_COMMAND_UI 通知，並將指派`COleCmdUI`物件。  
  
 `COleCmdUI` 允許的 DocObject 接收命令是源自於其容器的使用者介面 （例如 FileNew、 Open、 列印等等），並允許容器接收來自 DocObject 的使用者介面中的命令。 雖然`IDispatch`可以用來分派相同的命令，`IOleCommandTarget`提供更簡單的方式，來查詢，並執行，因為它會依賴一組標準的命令，通常不使用引數，而且不涉及任何類型資訊。 `COleCmdUI` 可用來啟用、 更新和設定其他屬性的 DocObject 使用者介面的命令。 當您想要叫用命令時，呼叫[COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。  
  
 如需 DocObjects 的詳細資訊，請參閱[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)並[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdocobj.h  
  
##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI  
 建構`COleCmdUI`與特定的使用者介面的命令相關聯的物件。  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>參數  
 *rgCmds*  
 支援與指定 GUID 相關聯的命令清單。 `OLECMD`命令旗標與結構產生關聯的命令。  
  
 *cCmds*  
 中的命令計數*rgCmds*。  
  
 *pGroup*  
 識別一組命令的 GUID 指標。  
  
### <a name="remarks"></a>備註  
 `COleCmdUI`物件提供的程式設計介面來更新 DocObject 使用者介面物件，例如功能表項目或控制列按鈕。 使用者介面物件可以是已啟用、 停用、 檢查，和/或透過清除`COleCmdUI`物件。  
  
##  <a name="enable"></a>  COleCmdUI::Enable  
 呼叫此函式可設定的命令旗標`COleCmdUI`OLECOMDF_ENABLED，告訴介面的命令是可用且處於啟用狀態，或清除命令旗標的物件。  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>參數  
 *bOn*  
 指出是否使用相關聯的命令`COleCmdUI`物件應該啟用或停用。 Nonzero 可讓命令0 會停用的命令。  
  
##  <a name="setcheck"></a>  COleCmdUI::SetCheck  
 呼叫此函式可設定狀態的開啟/關閉切換命令。  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>參數  
 *n*  
 值，判斷要設定的開啟/關閉切換狀態命令。 值為：  
  
|值|描述|  
|-----------|-----------------|  
|**1**|若要在設定的命令。|  
|**2**|以不確定; 設定的命令無法判定狀態，因為此命令的屬性上並關閉相關的選取範圍中的狀態。|  
|任何其他值|設定要關閉的命令。|  
  
##  <a name="settext"></a>  COleCmdUI::SetText  
 呼叫此函式來傳回命令的文字名稱或狀態字串。  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 *lpszText*  
 要搭配此命令的文字指標。  
  
## <a name="see-also"></a>另請參閱  
 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



