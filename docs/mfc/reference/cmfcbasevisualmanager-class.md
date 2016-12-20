---
title: "CMFCBaseVisualManager Class | Microsoft Docs"
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
  - "CMFCBaseVisualManager"
  - "CMFCBaseVisualManager.~CMFCBaseVisualManager"
  - "~CMFCBaseVisualManager"
  - "CMFCBaseVisualManager::~CMFCBaseVisualManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCBaseVisualManager destructor"
  - "CMFCBaseVisualManager class"
  - "CMFCBaseVisualManager class, 解構函式"
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCBaseVisualManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在衍生的視覺管理員和 Windows 佈景主題 API 之間的階層。  
  
 `CMFCBaseVisualManager` 載入 UxTheme.dll，如果有的話，和管理 Windows 佈景主題 API 方法的存取。  
  
 這個類別僅供內部使用。  
  
## 語法  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](../Topic/CMFCBaseVisualManager::CMFCBaseVisualManager.md)|建構和 `CMFCBaseVisualManager` 初始化物件。|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::DrawCheckBox](../Topic/CMFCBaseVisualManager::DrawCheckBox.md)|使用目前的 Windows 佈景主題，繪製核取方塊控制項。|  
|[CMFCBaseVisualManager::DrawComboBorder](../Topic/CMFCBaseVisualManager::DrawComboBorder.md)|使用目前的 Windows 佈景主題，將下拉式方塊的框線。|  
|[CMFCBaseVisualManager::DrawComboDropButton](../Topic/CMFCBaseVisualManager::DrawComboDropButton.md)|使用目前的 Windows 佈景主題，繪製下拉式方塊下拉式按鈕。|  
|[CMFCBaseVisualManager::DrawPushButton](../Topic/CMFCBaseVisualManager::DrawPushButton.md)|使用目前的 Windows 佈景主題，會繪製按鈕。|  
|[CMFCBaseVisualManager::DrawRadioButton](../Topic/CMFCBaseVisualManager::DrawRadioButton.md)|使用目前的 Windows 佈景主題，繪製選項按鈕控制項。|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](../Topic/CMFCBaseVisualManager::DrawStatusBarProgress.md)|繪製在狀態列控制項 \([CMFCStatusBar Class](../../mfc/reference/cmfcstatusbar-class.md)\) 的進度列使用目前 Windows 佈景主題。|  
|[CMFCBaseVisualManager::FillReBarPane](../Topic/CMFCBaseVisualManager::FillReBarPane.md)|使用目前的 Windows 佈景主題，填滿 Rebar 控制項的背景。|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](../Topic/CMFCBaseVisualManager::GetStandardWindowsTheme.md)|取得目前 Windows 佈景主題。|  
  
### 受保護的方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCBaseVisualManager::CleanUpThemes](../Topic/CMFCBaseVisualManager::CleanUpThemes.md)|在呼叫 `UpdateSystemColors`取得的所有控制代碼的 `CloseThemeData` 。|  
|[CMFCBaseVisualManager::UpdateSystemColors](../Topic/CMFCBaseVisualManager::UpdateSystemColors.md)|呼叫 `OpenThemeData` 取得要繪製之的各種控制項的控制代碼: 視窗中，將工具列，按鈕，依此類推。|  
  
## 備註  
 您不需要直接執行個體化這個類別的物件。  
  
 由於它是所有視覺管理員的基底類別，使用該指標，您可以呼叫 [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md)，取得指標目前視覺管理員，並存取 `CMFCBaseVisualManager` 的方法。  不過，在中，如果使用目前 Windows 佈景主題，您必須明確控制，使用 `CMFCVisualManagerWindows` 介面最好的做法。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## 需求  
 **標題:** afxvisualmanager.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)