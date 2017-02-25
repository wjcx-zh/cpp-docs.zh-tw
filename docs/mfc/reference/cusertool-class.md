---
title: "CUserTool Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CUserTool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserTool class"
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CUserTool Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用者工具是執行外部應用程式的功能表項目。  \[**自訂**\] 對話方塊 \([CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)\) 的 \[**工具**\] 索引標籤可讓使用者將使用者工具並對每個使用者工具指定名稱、命令、引數和初始目錄。  
  
## 語法  
  
```  
class CUserTool : public CObject  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CUserTool::CopyIconToClipboard](../Topic/CUserTool::CopyIconToClipboard.md)||  
|[CUserTool::DrawToolIcon](../Topic/CUserTool::DrawToolIcon.md)|以指定的矩形的使用者工具圖示。|  
|[CUserTool::GetCommand](../Topic/CUserTool::GetCommand.md)|傳回包含這個命令文字與使用者工具的字串。|  
|[CUserTool::GetCommandId](../Topic/CUserTool::GetCommandId.md)|傳回使用者工具之功能表項目的命令 ID。|  
|[CUserTool::Invoke](../Topic/CUserTool::Invoke.md)|執行命令與使用者工具。|  
|[CUserTool::Serialize](../Topic/CUserTool::Serialize.md)|讀取或寫入這個物件從或其中的檔案。  \(覆寫 [CObject::Serialize](../Topic/CObject::Serialize.md)\)。|  
|[CUserTool::SetCommand](../Topic/CUserTool::SetCommand.md)|設定與這個關聯命令使用者工具。|  
|[CUserTool::SetToolIcon](../Topic/CUserTool::SetToolIcon.md)|從應用程式載入使用者工具的圖示與工具。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CUserTool::LoadDefaultIcon](../Topic/CUserTool::LoadDefaultIcon.md)|載入使用者工具的預設圖示。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CUserTool::m\_strArguments](../Topic/CUserTool::m_strArguments.md)|使用者工具的命令列引數。|  
|[CUserTool::m\_strInitialDirectory](../Topic/CUserTool::m_strInitialDirectory.md)|使用者工具的初始目錄。|  
|[CUserTool::m\_strLabel](../Topic/CUserTool::m_strLabel.md)|在工具的顯示功能表項目的工具名稱。|  
  
## 備註  
 如需如何啟用應用程式的使用者工具的詳細資訊，請參閱 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)。  
  
## 範例  
 下列範例示範如何從 `CUserToolsManager` 物件的工具，設定 `m_strLabel` 成員變數，並將使用者工具中執行的應用程式。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/CPP/cusertool-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## 需求  
 **標題:** afxusertool.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)