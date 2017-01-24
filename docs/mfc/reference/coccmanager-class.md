---
title: "COccManager Class | Microsoft Docs"
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
  - "COccManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器 [C++], control site"
  - "CNoTrackObject class"
  - "COccManager class"
  - "自訂控制項 [MFC], sites"
ms.assetid: 7d47aeed-d1ab-48e3-b4cf-d429718e370a
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COccManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理各種自訂控制項的網站;實作時 `COleControlContainer` 和 `COleControlSite` 物件。  
  
## 語法  
  
```  
class COccManager : public CNoTrackObject  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COccManager::CreateContainer](../Topic/COccManager::CreateContainer.md)|建立 **COleContainer** 物件。|  
|[COccManager::CreateDlgControls](../Topic/COccManager::CreateDlgControls.md)|建立 ActiveX 控制項，將由 `COleContainer` 相關聯的物件。|  
|[COccManager::CreateSite](../Topic/COccManager::CreateSite.md)|建立 `COleClientSite` 物件。|  
|[COccManager::GetDefBtnCode](../Topic/COccManager::GetDefBtnCode.md)|擷取預設按鈕的程式碼。|  
|[COccManager::IsDialogMessage](../Topic/COccManager::IsDialogMessage.md)|決定對話訊息的目標。|  
|[COccManager::IsLabelControl](../Topic/COccManager::IsLabelControl.md)|判斷指定的控制項是否為控制項標籤。|  
|[COccManager::IsMatchingMnemonic](../Topic/COccManager::IsMatchingMnemonic.md)|判斷目前的助憶鍵是否符合指定之控制項的助憶鍵。|  
|[COccManager::OnEvent](../Topic/COccManager::OnEvent.md)|嘗試處理指定的事件。|  
|[COccManager::PostCreateDialog](../Topic/COccManager::PostCreateDialog.md)|釋出對話方塊建立期間配置的資源。|  
|[COccManager::PreCreateDialog](../Topic/COccManager::PreCreateDialog.md)|處理 ActiveX 控制項的對話方塊範本。|  
|[COccManager::SetDefaultButton](../Topic/COccManager::SetDefaultButton.md)|切換指定控制項的預設狀態。|  
|[COccManager::SplitDialogTemplate](../Topic/COccManager::SplitDialogTemplate.md)|從中指定的對話方塊樣板的通用控制項分隔所有現有的 ActiveX 控制項。|  
  
## 備註  
 基底類別， **CNoTrackObject**，是未記載的基底類別 \(位於 AFXTLS.H\)。  設計供 MFC 架構， **CNoTrackObject** 從類別衍生的類別會從記憶體遺漏偵測不受限於。  建議您不要直接從 **CNoTrackObject**衍生。  
  
## 繼承階層架構  
 `CNoTrackObject`  
  
 `COccManager`  
  
## 需求  
 **Header:** afxocc.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlSite Class](../../mfc/reference/colecontrolsite-class.md)   
 [COleControlContainer Class](../../mfc/reference/colecontrolcontainer-class.md)