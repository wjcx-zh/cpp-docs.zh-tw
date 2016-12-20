---
title: "如何：建立功能表、子功能表和捷徑功能表 | Microsoft Docs"
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
  - "命令列, 架構"
  - "功能表, 建立"
  - "功能表, 架構"
  - "命令, 功能表"
  - "功能表"
ms.assetid: 62004fd9-7f99-4f00-8d01-1dde53e23dbb
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# 如何：建立功能表、子功能表和捷徑功能表
若要將功能表加入 Visual Studio 整合式開發環境 \(IDE\) 中，VSPackage 必須針對命令群組功能表使用 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 架構。 命令群組功能表可透過元件和 IDE 來共用命令。 如需命令群組功能表的詳細資訊，請參閱 [VSPackages 如何新增使用者介面項目](../Topic/How%20VSPackages%20Add%20User%20Interface%20Elements.md)。  
  
 在 VSPackage 中，功能表是在 .vsct 檔的[功能表](../Topic/Menus%20Element.md)區段中所定義。 .vsct 檔會定義功能表、工具列、群組和命令。 命令是使用者按一下以執行功能的項目。 群組是命令的容器。 功能表是群組的容器。 若要建立基本功能表，您必須建立功能表、命令群組及至少一個命令。  
  
 功能表在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中有三種基本的顯示方式：  
  
-   作為主功能表列上的功能表。  
  
-   作為另一個功能表的子功能表。  
  
-   作為捷徑功能表 \(通常是透過按一下滑鼠右鍵來顯示\)。  
  
 本主題會示範如何建立各種功能表。 下列逐步解說也會示範如何執行這項作業：  
  
-   [將功能表加入至 Visual Studio 功能表列](../Topic/Adding%20a%20Menu%20to%20the%20Visual%20Studio%20Menu%20Bar.md)  
  
-   [將子功能表新增至功能表](../Topic/Adding%20a%20Submenu%20to%20a%20Menu.md)  
  
-   [工具視窗中加入快顯功能表](../Topic/Adding%20a%20Shortcut%20Menu%20in%20a%20Tool%20Window.md)  
  
### 建立功能表、子功能表或捷徑功能表  
  
1.  在您的專案中，按兩下 .vsct 檔在編輯器中加以開啟。  
  
     如果您的專案沒有 .vsct 檔，請新增一個檔案。 如果您要使用 Visual Studio Package 範本建立封裝，請選取 \[功能表命令\]；這樣做會產生 .vsct 檔。  
  
2.  在 `Symbols` 區段中，尋找包含群組和命令的 [GuidSymbol](../Topic/GuidSymbol%20Element.md) 項目。  
  
3.  為您要加入的每個功能表、群組或命令建立 [IDSymbol](../Topic/IDSymbol%20Element.md) 項目，如下列範例所示。  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     `GuidSymbol` 和 `IDSymbol` 項目的 `name` 屬性為每個新的功能表、群組或命令提供一組 GUID:ID。`GUID` 代表為 VSPackage 定義的命令集。 您可以定義多個命令集。 每組 GUID:ID 都必須是唯一的。  
  
4.  在 `Menus` 區段中定義新的功能表，如下所示：  
  
    1.  設定 `guid` 和 `id` 欄位，以符合新功能表的 GUID:ID。  
  
    2.  設定 `priority` 屬性。  
  
         .vsct 檔使用 `priority` 屬性來決定功能表與父群組中其他物件的相對位置。  
  
         具有較低優先權值的功能表會先顯示，再顯示具有較高優先權值的功能表。 允許重複的優先權值，但具有相同優先權之功能表的相對位置會取決於 VSPackages 在執行階段的處理順序，而且該順序無法預先決定。 省略 `priority` 屬性會將其值設定為 0。  
  
         請勿設定捷徑功能表的優先權，因為其位置取決於呼叫功能表的程式碼。  
  
    3.  針對功能表和子功能表，將 `type` 屬性設定為 `Menu`，這會描述一般功能表。 針對捷徑功能表，將 `type` 屬性設定為 `Context`。  
  
         如需其他有效功能表類型的說明 \(例如工具列和功能表控制器\)，請參閱[功能表項目](../Topic/Menu%20Element.md)。  
  
    4.  在功能表定義中，建立包含 [ButtonText](../Topic/ButtonText%20Element.md) 項目的[字串](../Topic/Strings%20Element.md)區段，以包含顯示在 IDE 中的功能表名稱，並建立 [CommandName](../Topic/CommandName%20Element.md) 項目，以包含用於存取 \[命令\] 視窗中功能表的命令名稱。  
  
         如果按鈕文字字串包含 '&' 字元，使用者可以按 ALT 鍵及 '&' 後面緊接的字元來開啟功能表。  
  
    5.  視需要加入命令旗標，以變更功能表的外觀和行為。 若要執行這個動作，請在功能表定義中加入 [CommandFlag](../Topic/Command%20Flag%20Element.md) 項目。 如需詳細資訊，請參閱[命令旗標的項目](../Topic/Command%20Flag%20Element.md)。  
  
5.  設定功能表的父代。 若為標準功能表或子功能表，請根據您的設計，透過下列其中一個方式來執行這個動作：  
  
    -   在 `Menu` 項目中，建立[父代](../Topic/Parent%20Element.md)項目，並將其 `guid` 和 `id` 欄位設定為裝載功能表之群組的 GUID:ID，又稱為*「主要父群組」*\(Primary Parent Group\)。 父群組可以是您在 `Symbols` 區段中建立的群組、來自另一個封裝的群組，或來自 IDE 的群組。 例如，若要將您的功能表加入 IDE 的最上層功能表列的 \[工具\] 功能表附近，請將父代設定為 guidSHLMainMenu:IDG\_VS\_MM\_TOOLSADDINS。  
  
         下列範例會示範 Visual Studio 功能表列中所顯示的功能表。  
  
         [!CODE [TopLevelMenu#01](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#01)]  
  
    -   如果使用命令位置來放置功能表，則可以省略 `Parent`。 在 `Symbols` 區段之前建立 [CommandPlacements](../Topic/CommandPlacements%20Element.md) 區段，然後新增具有功能表 GUID:ID、優先權和父代的 [CommandPlacement](../Topic/CommandPlacement%20Element.md)，如下列範例所示。  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         建立多個有相同 GUID:ID 但有不同父代的命令位置，會使功能表出現在多個位置。 如需詳細資訊，請參閱[CommandPlacements 項目](../Topic/CommandPlacements%20Element.md)。  
  
     標準功能表必須在 Visual Studio 功能表列上有一個群組作為其父代。 若為子功能表，父代必須是另一個功能表 \(工具列或其他功能表類型\) 上的群組。 若為要顯示的功能表或子功能表，父代必須裝載一個群組，其中包含至少一個作用中命令，或具有 `AlwaysCreate` 命令旗標集。  
  
     捷徑功能表沒有父代或命令位置。 相反地，這些功能表必須以程式碼啟用。 一般而言，以滑鼠右鍵按一下控制項介面時，即會啟用捷徑功能表作為回應。 下列範例會定義捷徑功能表。  
  
     [!CODE [ButtonGroup#06](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#06)]  
  
6.  在[群組](../Topic/Groups%20Element.md)區段中，建立[群組](../Topic/Group%20Element.md)項目以包含要在功能表中顯示的命令。`Symbols` 區段必須包含與新的 `Group` 項目 \(Element\) 具有相同 GUID:ID 的項目 \(Entry\)。  
  
    1.  設定群組的優先權，使其顯示在功能表上的所需位置。  
  
         功能表上每個群組的界限會顯示為水平線。  
  
    2.  將這個新群組的父代設定為您所建立之功能表的 GUID:ID。 這樣做會將命令群組放在功能表上。  
  
     下列範例中的群組會顯示在如先前範例所示的最上層功能表中。  
  
     [!CODE [TopLevelMenu#02](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#02)]  
  
     功能表可以同時包含命令和子功能表。 子功能表 \(有時稱為串聯功能表\) 只是功能表，但這是會加入另一個功能表群組中，並且只有在叫用其他功能表時才會公開的功能表。 下列範例所示的功能表放到最上層功能表中的群組之後，即成為子功能表。  
  
     [!CODE [TopLevelMenu#06](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#06)]  
  
7.  若要將命令加入功能表中，請在[按鈕](../Topic/Buttons%20Element.md)區段中建立命令項目，然後將每個項目的父代設定為群組的 GUID:ID。 每個[按鈕](../Topic/Button%20Element.md)項目都必須有對應至 `Symbols` 區段中某個項目的 GUID:ID。  
  
     使用每個按鈕項目的 `priority` 屬性，來指定命令在群組中顯示的順序。  
  
     下列範例會定義最上層功能表中所顯示的命令。  
  
     [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
     如需按鈕和功能表項目的詳細資訊，請參閱[Button 元素](../Topic/Button%20Element.md)。  
  
     如需如何在程式碼中實作功能表命令的相關資訊，請參閱[MenuCommand 對比 OleMenuCommand](../misc/menucommands-vs-olemenucommands.md)或本主題稍早所述的逐步解說。  
  
### 啟用捷徑功能表  
  
1.  取得捷徑功能表的 GUID:ID。 根據預設，封裝範本會在 PkgCmdID.cs 檔案中建立 `GuidList` 類別，來保存命令集的 GUID。 此範本也會在 PkgCmdId.cs 檔案中建立 `PkgCmdIdList` 類別，來保存範本中所宣告之命令的整數 ID 值。 範本完成之後，必須宣告捷徑功能表及任何其他命令。 下列範例會顯示這些宣告。  
  
     [!code-cs[TWShortcutMenu#12](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_8.cs)]  
  
     如果直接使用 GUID 和 ID 值，則可以省略這個步驟。 不過，建議您在此設定值以便閱讀。  
  
2.  附加至事件處理常式。 一般而言，捷徑功能表會附加至控制項介面的右鍵項目，如下列範例所示。  
  
     [!code-cs[TWShortcutMenu#43](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_9.cs)]  
  
     <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法會將控制項的相對點選位置轉換成螢幕位置。<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> 方法會顯示捷徑功能表。  
  
     含有事件處理常式的檔案必須包含 <xref:System.ComponentModel.Design> 命名空間以存取 <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> 類別，並包含 <xref:Microsoft.VisualStudio.Shell> 命名空間以存取 <xref:System.ComponentModel.Design.IMenuCommandService> 介面。  
  
     [!code-cs[TWShortcutMenu#41](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_10.cs)]  
  
## 請參閱  
 [MenuCommand 對比 OleMenuCommand](../misc/menucommands-vs-olemenucommands.md)   
 [VSCT XML 結構描述參考](../Topic/VSCT%20XML%20Schema%20Reference.md)   
 [擴充的功能表和命令](../Topic/Extending%20Menus%20and%20Commands.md)