---
title: "ICommandSource Interface | Microsoft Docs"
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
  - "ICommandSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandSource interface"
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: 24
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandSource Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理不同命令來源物件傳送的命令指派給使用者控制項。  
  
## 語法  
  
```  
interface class ICommandSource  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ICommandSource::AddCommandHandler](../Topic/ICommandSource::AddCommandHandler.md)|會將命令處理常式加入至命令來源物件。|  
|[ICommandSource::AddCommandRangeHandler](../Topic/ICommandSource::AddCommandRangeHandler.md)|將命令處理常式的群組加入命令來源物件。|  
|[ICommandSource::AddCommandRangeUIHandler](../Topic/ICommandSource::AddCommandRangeUIHandler.md)|加入使用者介面命令訊息處理常式的群組加入命令來源物件。|  
|[ICommandSource::AddCommandUIHandler](../Topic/ICommandSource::AddCommandUIHandler.md)|將使用者介面 \(UI\) 命令訊息處理常式加入至命令來源物件。|  
|[ICommandSource::PostCommand](../Topic/ICommandSource::PostCommand.md)|張貼一則訊息，而不用等候處理。|  
|[ICommandSource::RemoveCommandHandler](../Topic/ICommandSource::RemoveCommandHandler.md)|從命令來源物件移除命令處理常式。|  
|[ICommandSource::RemoveCommandRangeHandler](../Topic/ICommandSource::RemoveCommandRangeHandler.md)|從命令來源物件移除命令處理常式的群組。|  
|[ICommandSource::RemoveCommandRangeUIHandler](../Topic/ICommandSource::RemoveCommandRangeUIHandler.md)|從命令來源物件移除使用者介面命令訊息處理常式的群組。|  
|[ICommandSource::RemoveCommandUIHandler](../Topic/ICommandSource::RemoveCommandUIHandler.md)|從命令來源物件移除使用者介面命令訊息處理常式。|  
|[ICommandSource::SendCommand](../Topic/ICommandSource::SendCommand.md)|傳送訊息並等候它會在傳回之前處理作業。|  
  
## 備註  
 當您裝載 \(Host\) MFC 檢視時的使用者控制項， [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) 路由命令並更新命令 UI 訊息至使用者控制項允許它處理 MFC 命令 \(例如，框架功能表項目和工具列按鈕\)。  藉由實作 [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)，您提供給使用者控制項 `ICommandSource` 對物件的參考。  
  
 如需如何使用 `ICommandTarget` 的範例，請參閱 [如何：新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。  
  
 如需使用 Windows Form 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## 需求  
 **標題:** afxwinforms.h \(定義於組件\\ atlmfc \\ lib mfcmifc80.dll\)  
  
## 請參閱  
 [如何：新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)