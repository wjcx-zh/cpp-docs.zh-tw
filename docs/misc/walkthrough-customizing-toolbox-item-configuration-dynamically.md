---
title: "逐步解說：以動態方式自訂工具箱項目設定 | Microsoft Docs"
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
  - "工具箱 [Visual Studio SDK], 加入控制項 (自訂的格式)"
ms.assetid: 761f44b7-c748-4ff5-921f-fc4f71784b0e
caps.latest.revision: 45
caps.handback.revision: 45
manager: "douge"
---
# 逐步解說：以動態方式自訂工具箱項目設定
本逐步解說會示範 Managed VSPackage 如何提供 <xref:System.Drawing.Design.ToolboxItem> 物件的動態設定支援。  
  
> [!NOTE]
>  在 \[工具箱\] 加入自訂控制項最簡單的方式，是使用隨附於 Visual Studio SDK 的 \[工具箱控制項\] 範本。 本主題與進階工具箱開發有關。  
>   
>  如需如何使用範本建立工具箱控制項的詳細資訊，請參閱[如何：建立使用 Windows Forms 的 \[工具箱\] 控制項](../Topic/How%20to:%20Create%20a%20Toolbox%20Control%20That%20Uses%20Windows%20Forms.md)和[建立 WPF 工具箱控制項](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)。  
  
 本逐步解說會引導您完成下列步驟：  
  
1.  使用 <xref:System.ComponentModel.ToolboxItemAttribute> 和 <xref:System.Drawing.ToolboxBitmapAttribute> 類別，在 VSPackage 物件中加入並正確登錄所有的 \[工具箱\] 控制項。  
  
2.  建立下列兩個控制項，並將其各自的圖示加入 \[工具箱\] 中：  
  
    -   宣告相關聯預設 <xref:System.Drawing.Design.ToolboxItem> 的控制項。  
  
    -   宣告衍生自 <xref:System.Drawing.Design.ToolboxItem> 類別的相關聯自訂 \[工具箱\] 項目的控制項。  
  
3.  撰寫 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 的實作，並執行下列動作予以登錄：  
  
    1.  定義篩選類別，其衍生自 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 類別並指定這項實作會作用於 <xref:System.Drawing.Design.ToolboxItem> 執行個體。  
  
    2.  將參考篩選類別的 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> 套用到實作 VSPackage <xref:Microsoft.VisualStudio.Shell.Package> 類別的類別。  
  
4.  將 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 套用到實作 VSPackage <xref:Microsoft.VisualStudio.Shell.Package> 類別的類別，以將 VSPackage 登錄為 <xref:System.Drawing.Design.ToolboxItem> 物件的提供者。  
  
5.  在封裝載入時間，使用反映產生 VSPackage 提供的所有 <xref:System.Drawing.Design.ToolboxItem> 物件清單。  
  
6.  建立 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件的處理常式。 這樣可確保正確載入 VSPackage 的 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
7.  實作 VSPackage 的命令以強制重新初始化 \[工具箱\]。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../Topic/Visual%20Studio%20SDK.md)。  
  
## Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在 \[新增專案\] 對話方塊的三個不同位置：  
  
1.  位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。  
  
2.  位在 C\# 擴充性下。 專案的預設語言為 C\#。  
  
3.  位在其他專案類型擴充性下。 專案的預設語言為 C\+\+。  
  
## 建立 Managed VSPackage  
 請完成下面程序建立 Managed VSPackage。  
  
#### 建立 Managed VSPackage 提供工具箱項目  
  
1.  建立名為 `ItemConfiguration` 的 VSPackage。 如需詳細資訊，請參閱[逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  在 \[Visual Studio Package\] 範本中加入功能表命令。  
  
     在 Visual Basic 將命令命名為 `Initialize ItemConfigurationVB`，在 Visual C\# 為 `Initialize ItemConfigurationCS`。  
  
3.  如為 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]，請將下列命名空間加入已產生專案的匯入命名空間清單中：  
  
    -   Company.ItemConfiguration  
  
    -   系統  
  
    -   System.ComponentModel  
  
    -   System.Drawing  
  
    -   System.Windows.Forms  
  
4.  將參考加入 <xref:System.Drawing.Design?displayProperty=fullName> .NET Framework 元件中。  
  
 如果針對多種語言執行本逐步解說作業，您必須更新專案，以釐清產生的組件。  
  
#### 釐清 Visual Basic 和 Visual C\# Vspackage  
  
1.  針對 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]：  
  
    1.  開啟專案屬性並選取 \[應用程式\] 索引標籤。  
  
         將組件名稱變更為 `ItemConfigurationVB`，並將預設的命名空間變更為 `Company.ItemConfigurationVB`。  
  
    2.  選取 \[參考\] 索引標籤。  
  
         更新匯入的命名空間清單。  
  
         移除 Company.ItemConfiguration。  
  
         加入 Company.ItemConfigurationVB。  
  
2.  針對 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]：  
  
    1.  開啟專案屬性並選取 \[應用程式\] 索引標籤。  
  
         將組件名稱變更為 `ItemConfigurationCS`，並將預設的命名空間變更為 `Company.ItemConfigurationCS`。  
  
    2.  在程式碼編輯器中開啟 ItemConfigurationPackage 類別。  
  
         若要使用重構工具重新命名現有的命名空間，請以滑鼠右鍵按一下現有的命名空間名稱 `ItemConfiguration`，然後指向 \[重構\]，然後按一下 \[重新命名\]。 將名稱變更為 `ItemConfigurationCS`。  
  
3.  儲存所有變更。  
  
#### 測試產生的程式碼  
  
1.  在 Visual Studio 實驗登錄區中編譯並啟動 VSPackage。  
  
2.  在 \[工具\] 功能表上，按一下 \[初始化項目設定 VB\] 或 \[初始化項目設定 CS\]。  
  
     這樣會開啟訊息方塊，包含的文字指出已呼叫過封裝的功能表項目處理常式。  
  
3.  關閉 [!INCLUDE[vs_current_short](../misc/includes/vs_current_short_md.md)] 的實驗版本。  
  
## 建立工具箱控制項  
 在本節中，您要建立並登錄使用者控制項 `Control1`，宣告相關聯的預設 \[工具箱\] 項目。 您也要建立並登錄第二個使用者控制項 `Control2`，和相關聯的自訂 \[工具箱\] 項目，衍生自 <xref:System.Drawing.Design.ToolboxItem> 類別的 `Control2_ToolboxItem`。 如需如何撰寫 Windows Forms 控制項和 <xref:System.Drawing.Design.ToolboxItem> 類別的詳細資訊，請參閱[在設計階段開發 Windows Form 控制項](../Topic/Developing%20Windows%20Forms%20Controls%20at%20Design%20Time.md)。  
  
#### 建立預設和自訂的工具箱項目  
  
1.  請依照[逐步解說：自動載入工具箱項目](../misc/walkthrough-autoloading-toolbox-items.md)的指示建立預設的 \[工具箱\] 項目和自訂的 \[工具箱\] 項目，如下所示。  
  
    1.  完成「建立和預設 ToolboxItem 一起使用的 \[工具箱\] 控制項」程序。 更新 <xref:System.ComponentModel.DescriptionAttribute> 以參考這個專案。  
  
         因 `Control1` 類別而產生的程式碼應該類似下列程式碼。  
  
         [!code-cs[DynamicToolboxMembers#01](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_1.cs)]
         [!code-vb[DynamicToolboxMembers#01](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_1.vb)]  
  
    2.  完成「建立 \[工具箱\] 控制項以使用自訂的 ToolboxItem 衍生類別」程序。 更新 <xref:System.ComponentModel.DescriptionAttribute> 以參考這個專案。  
  
         因 `Control2` 和 `Control2_ToolboxItem` 類別而產生的程式碼應該類似下列程式碼。  
  
         [!code-vb[DynamicToolboxMembers#02](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_2.vb)]
         [!code-cs[DynamicToolboxMembers#02](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_2.cs)]  
  
2.  儲存檔案。  
  
## 內嵌點陣圖圖示  
 套用至每個控制項的 <xref:System.Drawing.ToolboxBitmapAttribute> 屬性會指定相關聯的控制項和圖示。 建立兩種控制項的點陣圖，並加以命名，如下所示：  
  
-   `Control1.bmp` 用於 `Control1` 類別。  
  
-   `Control2.bmp` 用於 `Control2` 類別。  
  
#### 為工具箱項目內嵌點陣圖圖示  
  
1.  在專案中加入新的點陣圖，如下所示：  
  
    1.  在**方案總管**中，以滑鼠右鍵按一下 VSPackage 專案，指向 \[加入\]，然後按一下 \[新增項目\]。  
  
    2.  在 \[加入新項目\] 對話方塊中，選取 \[點陣圖檔\]，然後輸入點陣圖的名稱。  
  
2.  使用點陣圖編輯器建立 16x16 的圖示，如下所示。  
  
    1.  在 \[**檢視**\] 功能表中，按一下 \[**屬性視窗**\]。  
  
    2.  在 \[屬性\] 視窗中，將 \[高度\] 和 \[寬度\] 設為 16。  
  
    3.  使用編輯器建立圖示影像。  
  
3.  在**方案總管**中，以滑鼠右鍵按一下點陣圖項目，然後按一下 \[屬性\]。  
  
4.  將 \[建置動作\] 屬性設為 \[內嵌資源\]。  
  
5.  儲存所有開啟的檔案。  
  
## 加入動態工具箱設定提供者  
 在本節中，您要建立並登錄實作 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 介面的類別。[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 使用並具現化這個類別來設定 \[工具箱\] 控制項。  
  
> [!NOTE]
>  因為 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 環境具現化 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 的實作執行個體，不在實作 VSPackage <xref:Microsoft.VisualStudio.Shell.Package> 的類別上實作 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 介面。  
  
#### 建立並登錄工具箱控制項設定物件  
  
1.  在**方案總管**中，將類別加入 ItemConfiguration 專案中，並命名為 `ToolboxConfig`。  
  
2.  在檔案中加入下列命名空間陳述式。  
  
     [!code-cs[DynamicToolboxMembers#03](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_3.cs)]
     [!code-vb[DynamicToolboxMembers#03](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_3.vb)]  
  
3.  確認 `ToolboxConfig` 類別是 `public`，並實作 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 介面。  
  
4.  將 <xref:System.Runtime.InteropServices.GuidAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> 套用至 `ToolboxConfig` 類別`.`  
  
    -   如為 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]，請使用 `"ItemConfigurationVB, Version=*, Culture=*, PublicKeyToken=*"` 的組件名稱。  
  
    -   如為 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]，請使用 `"ItemConfigurationCS, Version=*, Culture=*, PublicKeyToken=*"` 的組件名稱。  
  
     如此一來，可以限制 `ToolboxConfig` 類別處理 <xref:System.Drawing.Design.ToolboxItem> 物件，這是包含目前 VSPackage 的組件所提供的物件。  
  
     [!code-cs[DynamicToolboxMembers#04](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_4.cs)]
     [!code-vb[DynamicToolboxMembers#04](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_4.vb)]  
  
     您可以按一下 \[工具\] 功能表的 \[建立 GUID\] 產生 GUID。 選取 \[使用方括號格式\]，按一下 \[複製\]，然後在程式碼中貼上 GUID。 將關鍵字 `GUID` 變更成 `Guid`。  
  
5.  實作 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem> 介面的 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 方法，讓方法只對這兩個 <xref:System.Drawing.Design.ToolboxItem> 類別，即 `Control1` 和 `Control2` 作用。  
  
     <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 實作將 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 的執行個體套用到兩個 <xref:System.Drawing.Design.ToolboxItem> 物件，以便：  
  
    -   由 `Control1` 實作的 <xref:System.Drawing.Design.ToolboxItem> 僅在 \[工具箱\] 中提供，供處理 <xref:System.Windows.Forms.UserControl> 物件的設計師使用。  
  
    -   \[工具箱\] 不提供由 `Control2` 實作的 <xref:System.Drawing.Design.ToolboxItem>，供處理 <xref:System.Windows.Forms.UserControl> 物件的設計師使用。  
  
     [!code-cs[DynamicToolboxMembers#05](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_5.cs)]
     [!code-vb[DynamicToolboxMembers#05](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_5.vb)]  
  
## 修改 VSPackage 實作  
 VSPackage 的預設實作是由 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 封裝範本所提供，這個範本必須修改後才能執行下列動作：  
  
-   登錄為 \[工具箱\] 項目提供者。  
  
-   登錄提供 VSPackage 動態 \[工具箱\] 控制項設定的類別。  
  
-   使用 <xref:System.Drawing.Design.ToolboxService> 載入 VSPackage 組件提供的所有 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
-   處理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
#### 在 VSPackage 修改工具箱項目提供者的封裝實作  
  
1.  在程式碼編輯器中開啟 ItemConfigurationPackage 類別。  
  
2.  修改 `ItemConfigurationPackage` 類別的宣告，也就是解決方案中 <xref:Microsoft.VisualStudio.Shell.Package> 類別的實作。  
  
    1.  在檔案中加入下列命名空間陳述式。  
  
         [!code-vb[DynamicToolboxMembers#06](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_6.vb)]
         [!code-cs[DynamicToolboxMembers#06](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_6.cs)]  
  
    2.  若要將 VSPackage 登錄為提供 \[工具箱\] 項目，請將 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 套用至封裝。 若要將 `ToolboxConfig` 類別登錄為提供 \[工具箱\] 控制項動態組態、請將 <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemConfigurationAttribute> 套用至封裝。  
  
         [!code-vb[DynamicToolboxMembers#07](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_7.vb)]
         [!code-cs[DynamicToolboxMembers#07](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_7.cs)]  
  
        > [!NOTE]
        >  <xref:Microsoft.VisualStudio.Shell.ProvideToolboxItemsAttribute> 的唯一引數是 VSPackage 提供的 <xref:System.Drawing.Design.ToolboxItem> 版本。 您可以藉由變更此值，強制 IDE 載入 VSPackage，即使它有稍早快取的 <xref:System.Drawing.Design.ToolboxItem> 版本。  
  
    3.  在 `ItemConfiguration` 類別中建立兩個新的 `private` 欄位，如下所示：  
  
         名為 `ToolboxItemList` 的 <xref:System.Collections.ArrayList> 成員，保存 `ItemConfiguration` 類別管理的 <xref:System.Drawing.Design.ToolboxItem> 物件清單。  
  
         名為 `CategoryTab` 的 <xref:System.String>，包含 \[工具箱\] 索引標籤，這個索引標籤用來保存 `ItemConfiguration` 類別管理的 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
         [!code-vb[DynamicToolboxMembers#08](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_8.vb)]
         [!code-cs[DynamicToolboxMembers#08](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_8.cs)]  
  
     這項修改結果類似下列程式碼：  
  
     [!code-vb[DynamicToolboxMembers#09](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_9.vb)]
     [!code-cs[DynamicToolboxMembers#09](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_9.cs)]  
  
3.  定義 `OnRefreshToolbox` 方法處理 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件。  
  
     `OnRefreshToolbox` 方法使用 `ToolboxItemList` 欄位包含的 <xref:System.Drawing.Design.ToolboxItem> 物件清單，並執行下列操作：  
  
    -   從 `CategoryTab` 欄位所定義的 \[工具箱\] 索引標籤中，移除所有的 <xref:System.Drawing.Design.ToolboxItem> 物件 。  
  
    -   在 \[工具箱\] 索引標籤中加入 `ToolboxItemList` 欄位所列之全部 <xref:System.Drawing.Design.ToolboxItem> 物件的新執行個體。  
  
    -   將 \[工具箱\] 索引標籤設為使用中索引標籤。  
  
     [!code-vb[DynamicToolboxMembers#10](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_10.vb)]
     [!code-cs[DynamicToolboxMembers#10](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_10.cs)]  
  
4.  如為 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]，請在建構函式中，將 `OnRefreshToolbox` 方法登錄為 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxInitialized> 和 <xref:Microsoft.VisualStudio.Shell.Package.ToolboxUpgraded> 事件的事件處理常式。  
  
     [!code-cs[DynamicToolboxMembers#11](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_11.cs)]  
  
5.  藉由呼叫 <xref:System.Drawing.Design.ToolboxService?displayProperty=fullName> 類別的 <xref:System.Drawing.Design.ToolboxService.GetToolboxItems%2A> 方法，修改 `ItemConfigurationPackage` 中的 `Initialize` 方法填滿 `ToolboxItemList` 欄位。 \[工具箱\] 服務取得所有在目前執行組件中定義的 \[工具箱\] 項目類別。 \[工具箱\] 事件處理常式使用 `ToolboxItemList` 欄位載入 \[工具箱\] 項目。  
  
     在 `Initialize` 方法的結尾，加入下列程式碼。  
  
     [!code-vb[DynamicToolboxMembers#12](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_12.vb)]
     [!code-cs[DynamicToolboxMembers#12](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_12.cs)]  
  
    > [!NOTE]
    >  您可以開發一個機制，測試 VSPackage 或項目的版本，只有在 VSPackage 版本已變更或 <xref:System.Drawing.Design.ToolboxItem> 版本已變更時才更新，當做練習。  
  
## 初始化 \[工具箱\]  
  
#### 實作命令以初始化 \[工具箱\]  
  
-   在 `ItemConfigurationPackage` 類別中變更 `MenuItemCallBack` 方法，這是功能表項目的命令處理常式。  
  
     使用下列程式碼取代現有的 `MenuItemCallBack` 方法實作：  
  
     [!code-vb[DynamicToolboxMembers#13](../misc/codesnippet/VisualBasic/walkthrough-customizing-toolbox-item-configuration-dynamically_13.vb)]
     [!code-cs[DynamicToolboxMembers#13](../misc/codesnippet/CSharp/walkthrough-customizing-toolbox-item-configuration-dynamically_13.cs)]  
  
## 建置和執行解決方案  
 您可以使用在實驗登錄區中執行的 Visual Studio 執行個體，演練本逐步解說的產品。  
  
#### 演練本逐步解說  
  
1.  在 Visual Studio 中，按一下 \[建置\] 功能表上的 \[重建方案\]。  
  
2.  按 F5，在實驗登錄區中啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的第二個執行個體。  
  
     如需如何使用實驗登錄區的詳細資訊，請參閱[實驗執行個體](../Topic/The%20Experimental%20Instance.md)。  
  
3.  按一下 \[工具\] 功能表。  
  
     名為 \[初始化項目設定 VB\] 或 \[初始化項目設定 CS\] 的命令會出現在功能表上方，伴有數字 1 的圖示。  
  
4.  建立新的 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)] 或 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] Windows Forms 應用程式。  
  
     <xref:System.Windows.Forms.Form> 型的設計工具隨即出現。  
  
5.  將使用者控制項加入專案中。  
  
     使用者控制項設計工具隨即出現。  
  
6.  Pin 開啟 \[工具箱\]，在兩個設計檢視之間切換。  
  
     請注意，顯示及隱藏哪一個 \[工具箱\] 項目，取決於哪一個設計工具取得焦點。  
  
7.  將第一個 \[工具箱\] 項目拖曳至使用者控制項，將 `Control1` 的執行個體加入使用者控制項中。  
  
8.  將第二個 \[工具箱\] 項目拖曳至表單，將 `Control2` 的執行個體加入表單中。  
  
9. 建置 Windows 應用程式。  
  
     應用程式的使用者控制項現可於 \[工具箱\] 中取得。  
  
10. 將應用程式的使用者控制項加入表單中，然後重建及執行應用程式。  
  
     當應用程式執行時，按一下表單上的每一個控制項，以取得相關聯的訊息方塊。  
  
## 分析實作  
 因為 `assemblyFilter` 參數是存在於 <xref:Microsoft.VisualStudio.Shell.ProvideAssemblyFilterAttribute> 類別建構函式中，只有 `ToolboxConfg` 類別的 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 方法能讓本逐步解說所產生組件中的 <xref:System.Drawing.Design.ToolboxItem> 物件發生作用。  
  
 因此，每當 **ItemConfiguration 逐步解說**類別在 \[工具箱\] 中使用時，就會呼叫 `ToolboxConfg` 類別的 <xref:Microsoft.VisualStudio.Shell.IConfigureToolboxItem.ConfigureToolboxItem%2A> 方法，而 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 執行個體會套用在 `Control1` 和 `Control2` 所實作的 <xref:System.Drawing.Design.ToolboxItem> 物件。  
  
## 請參閱  
 [擴充工具箱](../misc/extending-the-toolbox.md)   
 [註冊工具箱支援功能](../misc/registering-toolbox-support-features.md)   
 [進階工具箱控制項開發](../misc/advanced-toolbox-control-development.md)   
 [工具箱逐步解說](../misc/toolbox-walkthroughs.md)