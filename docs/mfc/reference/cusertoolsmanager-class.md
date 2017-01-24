---
title: "CUserToolsManager Class | Microsoft Docs"
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
  - "CUserToolsManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserToolsManager class"
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUserToolsManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

維護物件的集合 [CUserTool Class](../../mfc/reference/cusertool-class.md) 在應用程式中。  使用者工具是執行外部應用程式的功能表項目。  `CUserToolsManager` 物件可讓使用者或開發人員加入新的使用者工具加入至應用程式。  它支援命令執行與使用者工具，因此，它還會將有關使用者的資訊工具在 Windows 登錄中。  
  
## 語法  
  
```  
class CUserToolsManager : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CUserToolsManager::CUserToolsManager](../Topic/CUserToolsManager::CUserToolsManager.md)|建構 `CUserToolsManager`。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CUserToolsManager::CreateNewTool](../Topic/CUserToolsManager::CreateNewTool.md)|建立新的使用者工具。|  
|[CUserToolsManager::FindTool](../Topic/CUserToolsManager::FindTool.md)|傳回指向與指定的命令 ID 的物件 `CMFCUserTool` .|  
|[CUserToolsManager::GetArgumentsMenuID](../Topic/CUserToolsManager::GetArgumentsMenuID.md)|傳回與 \[**自訂**\] 對話方塊的 \[**工具**\] 索引標籤的 \[**引數**\] 功能表的資源 ID。|  
|[CUserToolsManager::GetDefExt](../Topic/CUserToolsManager::GetDefExt.md)|傳回 \[**開啟的檔案。**\] 對話方塊的預設副檔名 \([CFileDialog::CFileDialog](../Topic/CFileDialog::CFileDialog.md)\) 在 \[**自訂**\] 對話方塊的 \[**工具**\] 索引標籤的 \[**命令**\] 欄位。|  
|[CUserToolsManager::GetFilter](../Topic/CUserToolsManager::GetFilter.md)|傳回 \[**開啟的檔案。**\] 對話方塊的檔案篩選條件 \([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\) 在 \[**自訂**\] 對話方塊的 \[**工具**\] 索引標籤的 \[**命令**\] 欄位。|  
|[CUserToolsManager::GetInitialDirMenuID](../Topic/CUserToolsManager::GetInitialDirMenuID.md)|傳回與 \[**自訂**\] 對話方塊的 \[**工具**\] 索引標籤的 \[**初始目錄**\] 功能表的資源 ID。|  
|[CUserToolsManager::GetMaxTools](../Topic/CUserToolsManager::GetMaxTools.md)|要傳回的使用者工具的最大數目可以在應用程式中配置。|  
|[CUserToolsManager::GetToolsEntryCmd](../Topic/CUserToolsManager::GetToolsEntryCmd.md)|傳回功能表項目預留位置的 ID 使用者工具命令的。|  
|[CUserToolsManager::GetUserTools](../Topic/CUserToolsManager::GetUserTools.md)|傳回使用者工具清單的參考。|  
|[CUserToolsManager::InvokeTool](../Topic/CUserToolsManager::InvokeTool.md)|執行與相關聯的應用程式具有指定的命令 ID. 的使用者工具|  
|[CUserToolsManager::IsUserToolCmd](../Topic/CUserToolsManager::IsUserToolCmd.md)|決定命令 ID 是否與使用者工具。|  
|[CUserToolsManager::LoadState](../Topic/CUserToolsManager::LoadState.md)|從 Windows 登錄載入有關使用者工具的相關資訊。|  
|[CUserToolsManager::MoveToolDown](../Topic/CUserToolsManager::MoveToolDown.md)|將指定的使用者工具下移使用者工具清單。|  
|[CUserToolsManager::MoveToolUp](../Topic/CUserToolsManager::MoveToolUp.md)|將指定的使用者工具在使用者工具清單。|  
|[CUserToolsManager::RemoveTool](../Topic/CUserToolsManager::RemoveTool.md)|從應用程式移除指定使用者的工具。|  
|[CUserToolsManager::SaveState](../Topic/CUserToolsManager::SaveState.md)|在 Windows 登錄中儲存有關使用者工具的相關資訊。|  
|[CUserToolsManager::SetDefExt](../Topic/CUserToolsManager::SetDefExt.md)|指定 \[**開啟的檔案。**\] 對話方塊的預設副檔名 \([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\) 在 \[**自訂**\] 對話方塊的 \[**工具**\] 索引標籤的 \[**命令**\] 欄位。|  
|[CUserToolsManager::SetFilter](../Topic/CUserToolsManager::SetFilter.md)|指定 \[**開啟的檔案。**\] 對話方塊的檔案篩選條件 \([CFileDialog Class](../../mfc/reference/cfiledialog-class.md)\) 在 \[**自訂**\] 對話方塊的 \[**工具**\] 索引標籤的 \[**命令**\] 欄位。|  
  
## 備註  
 若要結合使用者工具加入至您的應用程式，您必須:  
  
 1.  為使用者工具功能表項目保留功能表項目和關聯的命令 ID。  
  
 2.  為使用者在應用程式中定義的每個使用者工具保留執行命令 ID。  
  
 3.  呼叫 [CWinAppEx::EnableUserTools](../Topic/CWinAppEx::EnableUserTools.md) 方法並提供下列參數:功能表命令 ID、第一個使用者工具命令 ID 和最後一個使用者工具命令 ID.  
  
 應該只針對應用程式 `CUserToolsManager` 全域物件。  
  
 如需使用者工具的範例，請參閱 VisualStudioDemo 範例專案。  
  
## 範例  
 下列範例示範如何擷取 `CUserToolsManager` 對物件的參考以及如何建立新的使用者工具。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/CPP/cusertoolsmanager-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)  
  
## 需求  
 **標題:** afxusertoolsmanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CUserTool Class](../../mfc/reference/cusertool-class.md)