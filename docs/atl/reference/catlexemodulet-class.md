---
title: "CAtlExeModuleT Class | Microsoft Docs"
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
  - "ATL::CAtlExeModuleT<T>"
  - "CAtlExeModuleT"
  - "ATL.CAtlExeModuleT<T>"
  - "ATL::CAtlExeModuleT"
  - "ATL.CAtlExeModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlExeModuleT class"
ms.assetid: 82245f3d-91d4-44fa-aa86-7cc7fbd758d9
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlExeModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別表示應用程式的模組。  
  
## 語法  
  
```  
  
      template <  
   class T   
>  
class ATL_NO_VTABLE CAtlExeModuleT :  
   public CAtlModuleT< T >  
```  
  
#### 參數  
 `T`  
 從 `CAtlExeModuleT`衍生的類別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlExeModuleT::CAtlExeModuleT](../Topic/CAtlExeModuleT::CAtlExeModuleT.md)|建構函式。|  
|[CAtlExeModuleT::~CAtlExeModuleT](../Topic/CAtlExeModuleT::~CAtlExeModuleT.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlExeModuleT::InitializeCom](../Topic/CAtlExeModuleT::InitializeCom.md)|初始化 COM。|  
|[CAtlExeModuleT::ParseCommandLine](../Topic/CAtlExeModuleT::ParseCommandLine.md)|剖析命令列，並視需要進行註冊。|  
|[CAtlExeModuleT::PostMessageLoop](../Topic/CAtlExeModuleT::PostMessageLoop.md)|在訊息迴圈結束後，會呼叫這個方法。|  
|[CAtlExeModuleT::PreMessageLoop](../Topic/CAtlExeModuleT::PreMessageLoop.md)|這個方法會在輸入訊息迴圈之前呼叫。|  
|[CAtlExeModuleT::RegisterClassObjects](../Topic/CAtlExeModuleT::RegisterClassObjects.md)|註冊類別物件。|  
|[CAtlExeModuleT::RevokeClassObjects](../Topic/CAtlExeModuleT::RevokeClassObjects.md)|移除類別物件。|  
|[CAtlExeModuleT::Run](../Topic/CAtlExeModuleT::Run.md)|這個方法會在 EXE 模組的程式碼，以初始化執行訊息迴圈，並清除。|  
|[CAtlExeModuleT::RunMessageLoop](../Topic/CAtlExeModuleT::RunMessageLoop.md)|這個方法會實作訊息迴圈。|  
|[CAtlExeModuleT::UninitializeCom](../Topic/CAtlExeModuleT::UninitializeCom.md)|Uninitializes COM。|  
|[CAtlExeModuleT::Unlock](../Topic/CAtlExeModuleT::Unlock.md)|遞減模組的鎖定計數。|  
|[CAtlExeModuleT::WinMain](../Topic/CAtlExeModuleT::WinMain.md)|這個方法會實作需求的程式碼執行 EXE。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlExeModuleT::m\_bDelayShutdown](../Topic/CAtlExeModuleT::m_bDelayShutdown.md)|設定旗標以表示應該會關閉模組的延遲。|  
|[CAtlExeModuleT::m\_dwPause](../Topic/CAtlExeModuleT::m_dwPause.md)|用於的暫停時間值來確保所有物件在關閉之前發行。|  
|[CAtlExeModuleT::m\_dwTimeOut](../Topic/CAtlExeModuleT::m_dwTimeOut.md)|用於的逾時值延遲卸載模組。|  
  
## 備註  
 `CAtlExeModuleT` 表示應用程式 \(EXE\) 模組並包含支援建立可執行檔的程式碼，以處理命令列，註冊類別物件，執行訊息迴圈和清除在匯出。  
  
 會在 EXE 伺服程式的 COM 物件會持續建立和終結時，這個類別是設計來改善效能。  在釋放最後一個 COM 物件之後，用戶端等候 [CAtlExeModuleT::m\_dwTimeOut](../Topic/CAtlExeModuleT::m_dwTimeOut.md) 資料成員指定的持續期間。  如果沒有活動在這段時間 \(也就是 COM 物件沒有建立\)，請關閉處理序中初始化。  
  
 [CAtlExeModuleT::m\_bDelayShutdown](../Topic/CAtlExeModuleT::m_bDelayShutdown.md) 資料成員是用來判斷 EXE 旗標是否應該使用已定義的機制上面。  如果設定為 false，則模組會立即結束。  
  
 如需在 ATL 模組的詳細資訊，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md)。  
  
## 繼承階層架構  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlExeModuleT`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [ATLDuck 範例](../../top/visual-cpp-samples.md)   
 [CAtlModuleT Class](../../atl/reference/catlmodulet-class.md)   
 [CAtlDllModuleT Class](../../atl/reference/catldllmodulet-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)