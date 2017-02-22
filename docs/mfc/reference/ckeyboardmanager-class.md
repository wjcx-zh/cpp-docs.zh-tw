---
title: "CKeyboardManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CKeyboardManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CKeyboardManager class"
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CKeyboardManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理主框架視窗以及子框架視窗的快速鍵資料表。  
  
## 語法  
  
```  
class CKeyboardManager : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CKeyboardManager::CKeyboardManager](../Topic/CKeyboardManager::CKeyboardManager.md)|建構 `CKeyboardManager` 物件。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CKeyboardManager::CleanUp](../Topic/CKeyboardManager::CleanUp.md)|清除表快速鍵。|  
|[CKeyboardManager::FindDefaultAccelerator](../Topic/CKeyboardManager::FindDefaultAccelerator.md)|擷取指定的命令和視窗的預設快速鍵。|  
|[CKeyboardManager::IsKeyHandled](../Topic/CKeyboardManager::IsKeyHandled.md)|決定金鑰是由在快速鍵對應表中處理。|  
|[CKeyboardManager::IsKeyPrintable](../Topic/CKeyboardManager::IsKeyPrintable.md)|指示字元為可列印的。|  
|[CKeyboardManager::IsShowAllAccelerators](../Topic/CKeyboardManager::IsShowAllAccelerators.md)|指出功能表是否顯示命令或只有預設快速鍵的所有快速鍵。|  
|[CKeyboardManager::LoadState](../Topic/CKeyboardManager::LoadState.md)|從 Windows 登錄載入快速鍵資料表。|  
|[CKeyboardManager::ResetAll](../Topic/CKeyboardManager::ResetAll.md)|重新載入來自應用程式資源的快速鍵資料表。|  
|[CKeyboardManager::SaveState](../Topic/CKeyboardManager::SaveState.md)|快速鍵將資料表拖曳至 Windows 登錄中。|  
|[CKeyboardManager::ShowAllAccelerators](../Topic/CKeyboardManager::ShowAllAccelerators.md)|會針對每一個命令指定架構要顯示所有命令的所有快速鍵，或單一快速鍵。  這個方法不會影響只具有一個關聯的快速鍵的命令。|  
|[CKeyboardManager::TranslateCharToUpper](../Topic/CKeyboardManager::TranslateCharToUpper.md)|將字元轉換為它的上邊緣暫存器。|  
|[CKeyboardManager::UpdateAccelTable](../Topic/CKeyboardManager::UpdateAccelTable.md)|更新為新的快速鍵資料表的快速鍵資料表。|  
  
## 備註  
 這個類別的成員可讓您儲存和快速鍵資料表加入至 Windows 登錄中，使用範本來更新快速鍵資料表和尋找一個命令的預設快速鍵在框架視窗。  此外， `CKeyboardManager` 物件可讓您控制快速鍵如何顯示。  
  
 您無法以手動方式建立 `CKeyboardManager` 物件。  它將會由您的應用程式架構自動建立。  不過，您應該在您的應用程式中初始化程序呼叫 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md) 。  若要取得指標應用程式的鍵盤處理常式中，呼叫 [CWinAppEx::GetKeyboardManager](../Topic/CWinAppEx::GetKeyboardManager.md)。  
  
## 範例  
 下列範例示範如何擷取指標 `CKeyboardManager` 物件從 `CWinAppEx` 類別以及如何顯示所有快速鍵與功能表命令。  這個程式碼片段是 [自訂呼叫範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/CPP/ckeyboardmanager-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## 需求  
 **標題:** afxkeyboardmanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md)   
 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)