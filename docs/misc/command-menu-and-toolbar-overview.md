---
title: "命令、功能表和工具列概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "功能表基本項目 [Visual Studio SDK]"
  - "工具列基本項目 [Visual Studio SDK]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# 命令、功能表和工具列概觀
功能表和工具列會提供一種圖形方式，方便使用者存取 VSPackage 中的命令。 命令是完成工作 \(例如，列印文件、重新整理檢視，或建立新檔案\) 的功能。 功能表和工具列是一種圖形方式，方便向使用者呈現您的命令。 通常，相關的命令會一起聚集在相同的功能表或工具列上。  
  
-   功能表通常會顯示為聚集在整合式開發環境 \(IDE\) 或工具視窗頂端的一連串單字字串。 功能表也可以顯示為滑鼠右鍵事件的結果，並且指的是該內容中的快顯功能表。 按一下時，會展開功能表以顯示一個或多個命令。 按一下時，命令可以執行工作，或啟動包含其他命令的子功能表。 一些已知功能表名稱是 \[檔案\]、\[編輯\]、\[檢視\] 和 \[視窗\]。 如需詳細資訊，請參閱[擴充的功能表和命令](../Topic/Extending%20Menus%20and%20Commands.md)。  
  
-   工具列通常是數串的按鈕和其他控制項 \(例如下拉式方塊、清單方塊、文字方塊和功能表控制器\)。 所有工具列控制項都是與命令相關聯。 按一下工具列按鈕時，會啟動其相關聯的命令。 工具列按鈕通常會有圖示建議基礎命令 \(例如 \[列印\] 命令的印表機\)。 在下拉式清單控制項中，清單中的每個項目都是與不同的命令相關聯。 功能表控制器是一種混合體，其中，控制項的一邊是工具列按鈕，另一邊則是按一下時顯示其他命令的向下箭號。 如需詳細資訊，請參閱 [如何：建立工具視窗的工具列](../misc/how-to-create-toolbars-for-tool-windows.md) 與 [將圖示加入至功能表命令](../Topic/Adding%20Icons%20to%20Menu%20Commands.md)。  
  
-   建立命令時，也必須一併建立它的事件處理常式。 事件處理常式可判斷命令的顯示和啟用時間、可讓您修改其文字，並確保在啟動時適當地回應命令 \(路由遞送\)。 在大部分情況下，IDE 會使用 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 介面來處理命令。[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的命令會以階層方式路由遞送，即從最內層命令內容開始 \(根據本機選取範圍\) 到最外層內容 \(根據全域選取範圍\)。 加入主功能表的命令可立即用於指令碼編寫。 如需詳細資訊，請參閱[MenuCommand 對比 OleMenuCommand](../misc/menucommands-vs-olemenucommands.md)與[選擇內容物件](../Topic/Selection%20Context%20Objects.md)。  
  
 若要定義新的功能表和工具列，您必須以 Visual Studio 命令表 \(.vsct\) 檔案描述它們。 Visual Studio 封裝樣板會建立這個檔案以及必要項目，以支援您在樣板中所選取的任何命令、工具列和編輯器。 或者，您可以使用這裡所描述的 XML 結構描述來撰寫專屬 .vsct 檔案：[VSCT XML 結構描述參考](../Topic/VSCT%20XML%20Schema%20Reference.md)。  
  
 如需使用 .vsct 檔案的詳細資訊，請參閱 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../Topic/Visual%20Studio%20Command%20Table%20\(.Vsct\)%20Files.md)，或試用任何[使用者介面項目的逐步解說](../misc/walkthroughs-for-user-interface-elements.md)。  
  
 如需功能表和工具列的更詳細概觀，請參閱[命令設計](../Topic/Command%20Design.md)  
  
## 請參閱  
 [擴充的功能表和命令](../Topic/Extending%20Menus%20and%20Commands.md)   
 [命令、 功能表和工具列](../Topic/Commands,%20Menus,%20and%20Toolbars.md)   
 [Vspackage](../Topic/VSPackages.md)