---
title: "Item cannot be added to the Toolbox. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_NOTSUPPORTEDDATA"
  - "vs.message.0x800A0065"
ms.assetid: 69fa5e73-bbc6-462c-95ca-bf2ee32d43ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Item cannot be added to the Toolbox.
這個錯誤通常是發生在您嘗試將項目加入無法顯示捷徑圖示的工具箱。  
  
 工具箱可以顯示的項目包含：  
  
-   安裝在本機電腦上的控制項和 .NET Framework 元件。  
  
 **注意**：[!INCLUDE[vstecasp](../misc/includes/vstecasp_md.md)] Web form 的控制項和元件必須有「無限制」的 [AspNetHostingPermission.Level Property](https://msdn.microsoft.com/en-us/library/system.web.aspnethostingpermission.level.aspx) 顯示在工具箱中。  
  
-   從 Visual Studio 編輯器拖曳或貼上的選取文字，例如程式碼片段。  
  
 工具箱無法顯示的項目包含：  
  
-   Excel 活頁簿檔案。  
  
-   安裝在共用網路伺服器的 .NET Framework 組件。  
  
    > [!NOTE]
    >  從 UNC 路徑加入的組件是未完全受信任的，因此該組件並未具備足夠的權限可以顯示在工具箱中。  
  
### 若要更正這個錯誤  
  
1.  使用 \[**自訂工具箱**\] 對話方塊將安裝在本機電腦上的控制項或元件加入至使用中的 \[工具箱\] 索引標籤。  
  
     \-或\-  
  
2.  從 Visual Studio 編輯器將選取的文字拖曳或貼至工具箱。  
  
## 請參閱  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/zh-tw/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [工具箱](../Topic/Toolbox.md)