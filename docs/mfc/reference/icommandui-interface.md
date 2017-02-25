---
title: "ICommandUI Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ICommandUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandUI interface"
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ICommandUI Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理使用者介面、命令。  
  
## 語法  
  
```  
interface class ICommandUI  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[ICommandUI::Check](../Topic/ICommandUI::Check.md)|設定命令的使用者介面項目至適當的核取狀態。|  
|[ICommandUI::ContinueRouting](../Topic/ICommandUI::ContinueRouting.md)|呼叫命令路由機制繼續在路由處理常式的鏈結中目前的訊息。|  
|[ICommandUI::Enabled](../Topic/ICommandUI::Enabled.md)|啟用或停用命令的使用者介面項目。|  
|[ICommandUI::ID](../Topic/ICommandUI::ID.md)|取得 `ICommandUI` 物件所表示的使用者介面物件的 ID。|  
|[ICommandUI::Index](../Topic/ICommandUI::Index.md)|取得 `ICommandUI` 物件所表示的使用者介面物件的索引。|  
|[ICommandUI::Radio](../Topic/ICommandUI::Radio.md)|設定命令的使用者介面項目至適當的核取狀態。|  
|[ICommandUI::Text](../Topic/ICommandUI::Text.md)|設定使用者介面項目文字命令的。|  
  
## 備註  
 這個介面會處理使用者介面、命令的方法和屬性。  `ICommandUI`[CCmdUI Class](../../mfc/reference/ccmdui-class.md)類似，但是有一點例外，就是 `ICommandUI` 可搭配 .NET 元件互通的 MFC 應用程式使用。  
  
 在`ICommandUI``ON_UPDATE_COMMAND_UI` 管理員在 [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)衍生類別內使用。  當應用程式的使用者啟動 \(選項或按一下  功能表\) 時，每個功能表項目顯示為已啟用或停用。  每個功能表命令目標是藉由實作 `ON_UPDATE_COMMAND_UI` 管理員提供此資訊。  針對每個在應用程式的命令使用者介面物件，請使用 \[屬性\] 視窗建立每個處理常式的訊息對應 \(Message Map 輸入和函式原型。  
  
 如需 `ICommandUI` 介面運作方式的詳細資訊用於命令傳送，請參閱 [如何：新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。  
  
 如需使用 Windows Form 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 如需關於使用者介面命令運作方式的詳細資訊在 MFC 中處理，請參閱 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)。  
  
## 需求  
 **標題:** afxwinforms.h \(定義於組件\\ atlmfc \\ lib mfcmifc80.dll\)  
  
## 請參閱  
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)