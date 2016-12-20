---
title: "CCmdTarget Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCmdTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdTarget class"
  - "命令傳送, command targets"
  - "command targets"
  - "message maps, CCmdTarget base class"
  - "目標, 命令"
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫訊息對應 \(Message Map 結構的基底類別。  
  
## 語法  
  
```  
class CCmdTarget : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CCmdTarget::CCmdTarget](../Topic/CCmdTarget::CCmdTarget.md)|建構 `CCmdTarget` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)|顯示游標為沙漏游標。|  
|[CCmdTarget::DoOleVerb](../Topic/CCmdTarget::DoOleVerb.md)|會產生 OLE 動詞命令所指定的動作才會執行。|  
|[CCmdTarget::EnableAutomation](../Topic/CCmdTarget::EnableAutomation.md)|允許 `CCmdTarget` 物件的 OLE Automation。|  
|[CCmdTarget::EnableConnections](../Topic/CCmdTarget::EnableConnections.md)|啟用引發在連接點上的事件。|  
|[CCmdTarget::EnableTypeLib](../Topic/CCmdTarget::EnableTypeLib.md)|啟用目標型別程式庫。|  
|[CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)|回到上一個游標。|  
|[CCmdTarget::EnumOleVerbs](../Topic/CCmdTarget::EnumOleVerbs.md)|列舉物件的 OLE 動詞命令。|  
|[CCmdTarget::FromIDispatch](../Topic/CCmdTarget::FromIDispatch.md)|傳回指向 `CCmdTarget` 物件與 `IDispatch` 指標。|  
|[CCmdTarget::GetDispatchIID](../Topic/CCmdTarget::GetDispatchIID.md)|取得主要分派介面 ID.|  
|[CCmdTarget::GetIDispatch](../Topic/CCmdTarget::GetIDispatch.md)|傳回指向 `IDispatch` 物件與 `CCmdTarget` 物件。|  
|[CCmdTarget::GetTypeInfoCount](../Topic/CCmdTarget::GetTypeInfoCount.md)|擷取物件的型別資訊介面數目。|  
|[CCmdTarget::GetTypeInfoOfGuid](../Topic/CCmdTarget::GetTypeInfoOfGuid.md)|擷取對應到所指定 GUID 的型別描述。|  
|[CCmdTarget::GetTypeLib](../Topic/CCmdTarget::GetTypeLib.md)|取得指標型別程式庫。|  
|[CCmdTarget::GetTypeLibCache](../Topic/CCmdTarget::GetTypeLibCache.md)|取得型別程式庫快取。|  
|[CCmdTarget::IsInvokeAllowed](../Topic/CCmdTarget::IsInvokeAllowed.md)|啟用 Automation 方法引動過程。|  
|[CCmdTarget::IsResultExpected](../Topic/CCmdTarget::IsResultExpected.md)|如果自動化函式應傳回值，傳回非零。|  
|[CCmdTarget::OnCmdMsg](../Topic/CCmdTarget::OnCmdMsg.md)|路由命令和分派訊息。|  
|[CCmdTarget::OnFinalRelease](../Topic/CCmdTarget::OnFinalRelease.md)|在發行之後，清除最後 OLE 參考。|  
|[CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)|還原沙漏游標。|  
  
## 備註  
 訊息對應路由命令或訊息寫入您撰寫處理它們的成員函式。  \("命令與功能表項目、命令按鈕或快速鍵的訊息\)。  
  
 從 `CCmdTarget` 衍生自的主要畫面格類別包括、、 [CView](../../mfc/reference/cview-class.md)[CWinApp](../../mfc/reference/cwinapp-class.md)[CDocument](../../mfc/reference/cdocument-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)和 [CFrameWnd](../../mfc/reference/cframewnd-class.md)。  如果想要將新的類別可以處理訊息，從其中一個 `CCmdTarget`衍生類別的衍生類別。  您從 `CCmdTarget` 很少會直接從衍生類別。  
  
 如需路由命令的目標和 `OnCmdMsg` 的概觀，請參閱 [命令目標。](../../mfc/command-targets.md)、 [命令傳送](../../mfc/command-routing.md)和 [對應訊息。](../../mfc/mapping-messages.md)。  
  
 `CCmdTarget` 包括處理沙漏游標的顯示的成員函式。  當您預期會有一個命令會使用可觀的時間間隔加入至執行時，會顯示沙漏游標。  
  
 分派對應，類似於訊息對應，使用公開 OLE Automation `IDispatch` 功能。  透過這個介面，其他應用程式 \(例如 Visual Basic\) 可以呼叫您的應用程式。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [MFC ACDUAL 範例](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver Class](../../mfc/reference/coledispatchdriver-class.md)