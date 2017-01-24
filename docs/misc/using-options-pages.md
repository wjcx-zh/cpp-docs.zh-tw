---
title: "使用選項頁 | Microsoft Docs"
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
  - "工具選項頁 [Visual Studio SDK], 使用方式"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# 使用選項頁
[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Automation 模型提供 <xref:EnvDTE.DTE> 物件，讓 VSPackages 存取 \[工具\] 功能表的 \[選項\] 對話方塊。  
  
 \[選項\] 對話方塊中的頁面，通常使用 Automation 模型就可以存取，不論頁面是由 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 整合式開發環境 \(IDE\) 還是 VSPackage 所提供。 但是，凡事總有例外：  
  
-   \[動態說明\] 頁面的設定就不能以程式設計方式存取。 使用 Automation 模型可以控制 \[動態說明\] 功能，但控制必須直接在程式碼中完成。 如需詳細資訊，請參閱[How to: Control the Dynamic Help Window](http://msdn.microsoft.com/zh-tw/7f5777aa-c270-4058-a175-8ce8a4ed25eb)。  
  
-   對 \[字型和色彩\] 頁面設定的控制，要透過它自己的 API，不是透過 Automation 模型取得。 如需詳細資訊，請參閱[使用字型和色彩](../Topic/Using%20Fonts%20and%20Colors.md)。  
  
-   無法透過 Automation 模型取得語言特有的屬性。  
  
 不支援 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Automation 模型的 \[選項\] 頁面，被查詢時可能不會傳回自動化 <xref:EnvDTE.Properties> 集合。 如果傳回集合，也不會顯示所有功能。 如需如何管理這些功能的相關資訊，請參閱 [DTE 屬性集合](../Topic/DTE%20Properties%20Collections.md)。  
  
## 管理 \[選項\] 頁面  
 若要管理 \[選項\] 頁面，VSPackage 必須從 Automation 模型取得 <xref:EnvDTE.DTE> 物件。  
  
> [!NOTE]
>  當 VSPackage 使用 Automation 模型查詢和變更已安裝的 \[選項\] 頁面設定時，不會擴充 IDE 功能。 因此，封裝不必實作自動化物件。  
  
 若要透過 Automation 模型取得 <xref:EnvDTE.DTE> 物件，請呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 方法並提供 `SID_SDTE` 的服務識別碼引數和 `IID__DTE` 的介面引數，如下所示。  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 若要使用 Managed Package Framework \(MPF\) 取得 <xref:EnvDTE.DTE> 物件，請呼叫 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 方法並提供類型 <xref:Microsoft.VisualStudio.Shell.Interop.SDTE> 的參數 `serviceType`。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 \[選項\] 頁面由兩個識別項指定。 第一個識別項是指出包含 \[選項\] 頁面資料夾的字串。 第二個識別項是指出該資料夾中特定項目的字串。 這些稱為 \[選項\] 頁面分類和子分類，或其主題和副主題。  
  
 例如，處理 Basic 程式碼的文字編輯器設定，和 \[文字編輯器\] 資料夾的 \[Basic\] 成員一樣，都在瀏覽窗格中。 分類的識別項是 `TextEditor`，其子分類是 `Basic`，而 \[選項\] 頁面本身則是 `TextEditor.Basic` 頁面。  
  
> [!NOTE]
>  因為當地語系化和其他的原因，顯示在 \[選項\] 頁面的名稱可能和用做分類和子分類識別項的字串不同。 您可能必須使用自動化查詢 IDE，才能取得正確的識別項，如果它們不是記錄在其他位置。 登錄位置是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS 版本\>*\\AutomationProperties，這裡的 *\<VS 版本\>* 是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 發行版次的版本號碼。 如需詳細資訊，請參閱[註冊工具選項頁面](../misc/registering-custom-options-pages.md)。  
  
 您可以使用下列範例，透過 Automation 模型取得 `TextEditor.Basic` 頁面的屬性。  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 若要使用 MPF 取得屬性，請使用 <xref:EnvDTE._DTE.Properties%2A> 方法。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 <xref:EnvDTE.Properties.Item%2A> 方法會傳回來自 <xref:EnvDTE.Properties> 集合的個別設定，作為 <xref:EnvDTE.Property> 物件。  
  
 就像使用分類和子分類一樣，每個設定都有唯一字串的識別項。 例如，`TextEditor.Basic` 頁面上的 \[定位點大小\] 設定是由字串 `TabSize` 識別。  
  
> [!NOTE]
>  因為當地語系化和其他的原因，顯示在 \[選項\] 頁面的名稱可能和用做設定識別項的字串不同。 您可能必須使用自動化查詢 IDE，才能取得正確的識別項，如果它們不是記錄在其他位置。  
  
 您可以使用 <xref:EnvDTE.Properties> 集合的 <xref:EnvDTE.Properties.Item%2A> 方法傳回的 <xref:EnvDTE.Property> 物件的 <xref:EnvDTE.Property.Value%2A>，查詢和變更設定狀態。  
  
 例如，若要透過 Automation 模型在 `TextEditor.Basic` 頁面設定 \[定位點大小\] 設定，請使用下例傳回的 <xref:EnvDTE.Properties> 物件。  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 下例示範如何使用 MPF 更新 \[定位點大小\] 設定。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 如需詳細資訊，請參閱[控制選項設定](../Topic/Controlling%20Options%20Settings.md)。  
  
## 保存 \[選項\] 頁面設定  
 IDE 會實作完全支援 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Automation 模型之 \[選項\] 頁面的狀態持續性。  
  
 當使用者按一下 \[工具\] 功能表上的 \[匯入\/匯出設定\] 命令時，會自動儲存 \(或擷取\) IDE 所含頁面的設定。  
  
 您可以啟用自訂的 \[選項\] 頁面使用此自動持續性支援，只要將 `ProfileSave` 旗標加入 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ *\<VS 版本\>*\\AutomationProperties 下的自訂 \[選項\] 頁面的登錄項目，這裡的 *\<VS 版本\>* 是 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 發行版次的版本號碼。 如需詳細資訊，請參閱[註冊工具選項頁面](../misc/registering-custom-options-pages.md)。  
  
## 請參閱  
 [使用 Interop 組件建立選項頁面](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [建立選項頁](../Topic/Creating%20Options%20Pages.md)   
 [使用自動化建立選項頁面](../misc/creating-options-pages-by-using-automation.md)   
 [控制選項設定](../Topic/Controlling%20Options%20Settings.md)   
 [註冊工具選項頁面](../misc/registering-custom-options-pages.md)   
 [開啟選項頁面](../misc/opening-an-options-page.md)   
 [擴充使用者設定和選項](../Topic/Extending%20User%20Settings%20and%20Options.md)