---
title: "開啟選項頁面 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "開啟選項頁面"
  - "工具選項"
  - "選項頁面"
ms.assetid: 6f24cbfa-288a-4a57-831b-bc82587de255
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# 開啟選項頁面
您可以透過程式設計方式顯示選項頁面，以便您的封裝使用者可以在安裝期間進行設定。 若要在安裝封裝之後變更設定，使用者仍然可以使用 \[選項\] 對話方塊來存取選項頁面。  
  
### 顯示自訂選項頁面  
  
1.  建立選項頁面。 如需詳細資訊，請參閱[建立選項頁](../Topic/Creating%20Options%20Pages.md)。  
  
2.  將 `typeof` 關鍵字套用至定義選項頁面的類別名稱，以取得選項頁面的 <xref:System.Type>。  
  
3.  使用選項頁面的 <xref:System.Type> 作為參數來呼叫 <xref:Microsoft.VisualStudio.Shell.Package.ShowOptionPage%2A> 方法。  
  
     下列範例顯示名為 **HelloWorldOptions** 的選項頁面。  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/CSharp/opening-an-options-page_1.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#5](../misc/codesnippet/VisualBasic/opening-an-options-page_1.vb)]  
  
### 顯示由 Visual Studio 定義的選項頁面  
  
1.  在登錄子機碼 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\9.0\\ToolsOptionsPages\\ 中，尋找您要顯示的選項頁面節點，然後複製其 GUID，這是頁面索引鍵的值。  
  
2.  建立以常數 <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> 和 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> 為參數的 <xref:System.ComponentModel.Design.CommandID> 執行個體。  
  
     這會指定 \[選項\] 對話方塊。  
  
3.  使用 <xref:System.ComponentModel.Design.CommandID> 執行個體和 GUID 字串作為參數來呼叫 <xref:System.ComponentModel.Design.MenuCommandService.GlobalInvoke%2A> 方法。  
  
     下列範例顯示 \[文字編輯器\] 選項頁面的 \[一般\] 索引標籤。  
  
     [!code-cs[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/CSharp/opening-an-options-page_2.cs)]
     [!code-vb[UI_UserSettings_ToolsOptionPages#6](../misc/codesnippet/VisualBasic/opening-an-options-page_2.vb)]