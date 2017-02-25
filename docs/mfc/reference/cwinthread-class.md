---
title: "CWinThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinThread 類別"
  - "執行緒 [MFC], 建立執行緒"
  - "執行緒 [MFC], 安全"
  - "背景工作執行緒"
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CWinThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表應用程式內執行的執行緒。  
  
## 語法  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CWinThread::CWinThread](../Topic/CWinThread::CWinThread.md)|建構 `CWinThread` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWinThread::CreateThread](../Topic/CWinThread::CreateThread.md)|啟動 `CWinThread` 物件的執行。|  
|[CWinThread::ExitInstance](../Topic/CWinThread::ExitInstance.md)|清除的覆寫，當您執行緒終止。|  
|[CWinThread::GetMainWnd](../Topic/CWinThread::GetMainWnd.md)|擷取指標為執行緒的主視窗。|  
|[CWinThread::GetThreadPriority](../Topic/CWinThread::GetThreadPriority.md)|取得目前執行緒的優先權。|  
|[CWinThread::InitInstance](../Topic/CWinThread::InitInstance.md)|執行緒會初始化執行個體的覆寫。|  
|[CWinThread::IsIdleMessage](../Topic/CWinThread::IsIdleMessage.md)|特殊資訊的檢查。|  
|[CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md)|執行執行緒特定的閒置 \(Idle\) 時間處理的覆寫。|  
|[CWinThread::PostThreadMessage](../Topic/CWinThread::PostThreadMessage.md)|訊息發佈至另一個 `CWinThread` 物件。|  
|[CWinThread::PreTranslateMessage](../Topic/CWinThread::PreTranslateMessage.md)|篩選訊息，然後才會分派給 Windows 函式 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934)之前。|  
|[CWinThread::ProcessMessageFilter](../Topic/CWinThread::ProcessMessageFilter.md)|攔截特定訊息，並在到達應用程式。|  
|[CWinThread::ProcessWndProcException](../Topic/CWinThread::ProcessWndProcException.md)|攔截執行緒的訊息和命令處理常式所擲回的所有未處理的例外狀況。|  
|[CWinThread::PumpMessage](../Topic/CWinThread::PumpMessage.md)|包含執行緒的訊息迴圈。|  
|[CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md)|減少執行緒的暫停次數。|  
|[CWinThread::Run](../Topic/CWinThread::Run.md)|執行緒的控制項功能與訊息提取。  自訂預設訊息迴圈的覆寫。|  
|[CWinThread::SetThreadPriority](../Topic/CWinThread::SetThreadPriority.md)|設定目前執行緒的優先權。|  
|[CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md)|將執行緒的暫停次數。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CWinThread::operator HANDLE](../Topic/CWinThread::operator%20HANDLE.md)|擷取 `CWinThread` 物件的控制代碼。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CWinThread::m\_bAutoDelete](../Topic/CWinThread::m_bAutoDelete.md)|指定是否要終結物件在執行緒結束。|  
|[CWinThread::m\_hThread](../Topic/CWinThread::m_hThread.md)|out 目前執行緒的控制代碼。|  
|[CWinThread::m\_nThreadID](../Topic/CWinThread::m_nThreadID.md)|目前執行緒的 ID。|  
|[CWinThread::m\_pActiveWnd](../Topic/CWinThread::m_pActiveWnd.md)|指標容器應用程式的主視窗，當一個 OLE 伺服器是就地啟動。|  
|[CWinThread::m\_pMainWnd](../Topic/CWinThread::m_pMainWnd.md)|保留的指標\) 至應用程式的主視窗。|  
  
## 備註  
 從 `CWinApp`衍生的物件通常會提供主執行緒， `CWinApp``CWinThread`從衍生。  其他 `CWinThread` 物件允許在特定應用程式中的多個執行緒。  
  
 具有 `CWinThread` 支援執行緒的兩種一般型別:背景工作執行緒和使用者介面執行緒。  背景工作執行緒沒有訊息幫浦 \(Message Pump\):例如，報表應用程式執行計算的背景執行緒。  使用者介面執行緒會從系統接收的訊息幫浦 \(Message Pump\) 和處理訊息。  類別和從其衍生的[CWinApp](../../mfc/reference/cwinapp-class.md) 是使用者介面執行緒的範例。  其他使用者介面執行緒可以直接從 `CWinThread`也衍生自。  
  
 類別 `CWinThread` 物件為執行緒的過程通常存在。  如果您要修改此行為，請設定為 [m\_bAutoDelete](../Topic/CWinThread::m_bAutoDelete.md)**否**。  
  
 `CWinThread` 類別需要完整執行您的程式碼和 MFC 安全執行緒。  這個架構所使用的執行緒區域資料維護執行緒特定的資訊 `CWinThread` 由物件處理。  因此任何的執行緒必須使用 MFC 建立與管理執行緒區域資料的 `CWinThread` 的相依性，請使用 MFC。  例如，執行階段函式來建立的執行緒 [\_beginthread， \_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) 無法使用任何 MFC API。  
  
 若要建立執行緒，請呼叫 [AfxBeginThread](../Topic/AfxBeginThread.md)。  有兩種格式，取決於您是否要將背景工作執行緒或使用介面執行緒。  如果您想要使用介面執行緒，請傳遞至 `AfxBeginThread` 指標至 `CWinThread``CRuntimeClass` 衍生類別。  如果您想要建立背景工作執行緒，請傳遞至 `AfxBeginThread` 指標控制函式和參數傳遞至控制項的功能。  對於兩個背景工作執行緒和使用者介面執行緒，您可以指定修改優先權、堆疊大小、建立旗標和安全性屬性的選擇性參數。  `AfxBeginThread` 會傳回指向您的新 `CWinThread` 物件。  
  
 而不是呼叫 `AfxBeginThread`，您可以建構 `CWinThread`衍生物件然後呼叫 `CreateThread`。  如果要重複使用在執行緒上執行的建立和終止的之間， `CWinThread` 物件以兩個階段建構方法。  
  
 如需 `CWinThread`的相關資訊，請參閱 Microsoft 知識庫文件 [使用 C\+\+ 和 MFC 的多執行緒](../../parallel/multithreading-with-cpp-and-mfc.md)、 [多執行緒:建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)、 [多執行緒:建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)和 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)