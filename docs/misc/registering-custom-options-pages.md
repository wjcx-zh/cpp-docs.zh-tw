---
title: "註冊工具選項頁面 | Microsoft Docs"
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
  - "註冊, 自訂 [工具選項] 頁面"
  - "[工具選項] 頁面 [Visual Studio SDK], 註冊"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# 註冊工具選項頁面
對於**工具選項**能讓使用者和支援自動化的頁面上，必須以適當地註冊[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\)。  
  
 **工具選項**受管理的套件架構為基礎的網頁會藉由套用的執行個體登錄<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>來提供頁面的 VSPackage。  自動化支援表示藉由設定<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>屬性，以`true`。  
  
## 工具選項頁註冊  
 整合自訂的**工具選項**頁面與[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]需要登錄項目中的下列位置建立： HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages，其中 *\<Version\>* 版本的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]、 例如 8.0。  
  
 項目都與分類的主索引鍵 \(`<PageCategory>`\) 的**工具選項**頁面和子機碼包含在網頁的子類別的名稱 \(`<PageSubCategory>`\)。  
  
 例如， **工具選項**字串，用來識別網頁 **TextEditor.Basic**，具有登錄機碼`<PageCategory>`\= textEditor 子機碼的`<PageSubCategory>`\= 基本。  
  
 下面，是結構的登錄項目：  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\  
  
 `<PageCategory>` \= '\#12345'  
  
 封裝 \= ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 ResourcePackage \= ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}'  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 網頁 \= ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 封裝 \= ' {AAAAAA AAAA AAAA AAAA AAAAAAAAA}'  
  
 ResourcePackage \= ' {BBBBBB BBBB BBBB BBBB BBBBBBBBB}'  
  
 NoShowAllView \= 0\/1  
  
 下表列出的值低於 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\`<PageCategory>`。  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|自訂標準的類別名稱， **工具選項**頁面|機碼的名稱， `<PageCategory>`，是標準的非當地語系化的分類名稱**工具選項**頁面。 **Note:**  支援自動化時，標準非當地語系化的分類和子類別名稱用來取得**工具選項**網頁的<xref:EnvDTE.Properties>集合。  如需詳細資訊，請參閱 [使用選項頁](../misc/using-options-pages.md)。 <br /><br /> 受管理的封裝架構中，為基礎的實作`<PageCategory`\> 您可以從取得`categoryName`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。<br /><br /> 金鑰可以是空的或者也可以包含參考 ID 為實作的附屬 DLL 中當地語系化的字串。<br /><br /> 受管理的套件架構為基礎的實作，這個值取自`categoryResourceID`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。|  
|封裝|REG\_SZ|GUID|GUID 的實作自訂的 VSPackage **工具選項**頁面。<br /><br /> 受管理的套件架構使用根據實作<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用反映來取得這個值。|  
|ResourcePackage|REG\_SZ|GUID|選擇項。<br /><br /> 如果實作 VSPackage 未提供這些附屬 DLL 包含當地語系化字串。<br /><br /> 受管理的封裝架構會使用反映來取得正確的資源套件中，所以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>並不會設定此引數。|  
  
 下表列出的值低於 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages\\`<PageCategory>`\\`<PageSubCategory>`。  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|自訂標準子類別名稱**工具選項**頁面|機碼的名稱， `<PageSubCategory`\>，是正式非當地語系化名稱**工具選項**頁面子類別。 **Note:**  支援自動化時，標準非當地語系化的分類和子類別名稱用來取得**工具選項**網頁的<xref:EnvDTE.Properties>集合。  如需詳細資訊，請參閱 [使用選項頁](../misc/using-options-pages.md)。 <br /><br /> 受管理的封裝架構中，為基礎的實作`<PageSubegory`\> 您可以從取得`pageName`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。<br /><br /> 金鑰可以是空的或者也可以包含在附屬 DLL 的實作中的當地語系化字串的參考 ID。<br /><br /> 受管理的套件架構為基礎的實作，這個值取自`pageNameResourceID`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。|  
|頁面|REG\_SZ|GUID|實作自訂的物件 GUID **工具選項**頁面。<br /><br /> 實作根據受管理的套件架構使用<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用建構函式的`pageType`引數包含 VSPackage 的<xref:System.Type> ，並反映來取得這個值。|  
|封裝|REG\_SZ|GUID|受管理的套件架構使用根據實作<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用反映來取得這個值。|  
|ResourcePackage|REG\_SZ|GUID|選擇項。<br /><br /> 如果實作 VSPackage 未提供這些附屬 DLL 包含當地語系化字串。<br /><br /> 受管理的封裝架構會使用反映來取得正確的資源 DLL，所以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>並不會設定此引數。|  
|NoShowAllView|REG\_DWORD|0 或 1|選擇項。<br /><br /> 指出是否指定**工具選項** 的複雜 \(預設值\) 檢視中顯示網頁的 **工具選項**的網頁。  支援程式設計環境，例如 Visual Basic，具有特殊**工具選項**彙總的一般設定值，來為使用者提供的選項特製化的簡化檢視的網頁。<br /><br /> 如果呼叫完成項目是不是零， **工具選項**頁面沒有出現在複雜的檢視。<br /><br /> 如需詳細資訊，請參閱[選項對話方塊](../Topic/Options%20Dialog%20Box%20\(Visual%20Studio\).md)。<br /><br /> 受管理的套件架構為基礎的實作可以設定此值，藉由設定<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A>屬性，以`true`在<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。|  
  
 VSPackage 或單一 interop 組件為基礎的物件可能會實作一個以上的**工具選項**頁面。  每一個實作需要有新的項目，在 HKLM\\Software\\Microsoft\\VisualStudio\\*\<Version\>*\\ToolsOptionsPages。  
  
 與受管理套件架構執行個體化物件提供**工具選項** \] 頁面上，每個網頁都應該有它自己的實作物件，獨立於 VSPackage 的實作<xref:Microsoft.VisualStudio.Shell.Package>。  
  
## Automation 支援  
 如果 automation 支援用來實作**工具選項** \] 頁面上，它必須登錄本身為自動化提供者。  屬性管理、 使用自動化，並使用它的保存性機制來儲存**工具選項**頁面狀態，它必須登錄本身做為`AutomationProperty`提供者。  
  
### 暫存器為自動化提供者 \(僅適用於 Interop 組件為基礎的工具選項頁\) VSPackage  
 **工具選項** interop 組件為基礎的網頁會實作為 VSPackage 的實作類別的一部分。  
  
 如此一來，如果**工具選項**頁面是為了支援自動化，interop 的 assembly–based VSPackage 必須先註冊為自動化提供者。  
  
> [!NOTE]
>  獨立實作的 VSPackage 物件所提供的受管理的封裝架構中的自動化支援。  如果該物件支援自動化，這透過註冊<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>屬性的<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。  
  
 註冊 VSPackage，因為自動化提供者是 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ 的表單的項目*\<Version\>*\\Packages\\*\<PackageGUID\>*\\Automation，其中 *\<Version\>* 版本的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] \(例如，8.0\) 和 *\<PackageGUID\>* VSPackage 實作 automation 物件的 guid。  
  
> [!NOTE]
>  根路徑的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>* 可覆寫其他的根初始化 Visual Studio 命令介面時。  如需詳細資訊，請參閱 [命令列參數](../Topic/Command-Line%20Switches%20\(Visual%20Studio%20SDK\).md)。  
  
 登錄項目的結構是：  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\Packages\\*\<PackageGUID\>*\\Automation  
  
 `<AutomationObjectName>`  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|Automation|REG\_SZ|未定義|未定義。<br /><br /> 此機碼存在，表示 VSPackage 參照到的 *\<PackageGUID\>* 支援自動化。<br /><br /> 此欄位可用來儲存文件。<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>會自動建立此機碼來管理的套件架構為基礎的應用程式。|  
|`<AutomationObjectName>`|REG\_SZ|所提供的 automation 物件的正式名稱|索引鍵的名稱才適宜。  它使用於自動化作業。<br /><br /> 此欄位可用來儲存文件。<br /><br /> 受管理的套件架構為基礎的實作，此機碼名稱由`name`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>建構函式。<br /><br /> 如果<xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute>建構函式具有有效的字串，提供給其<xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A>屬性，這個值會插入在這裡。|  
  
### 註冊為支援自動化的工具選項頁  
 同時管理套件 Framework– 和 interop assembly–based 實作**工具選項** 頁面必須註冊才能自動化存取 **工具選項**頁面。  這包括自動化屬性保存性機制，以逐頁瀏覽存取<xref:EnvDTE>。  這是不受影響的 VSPackage 本身為自動化服務提供者註冊。  
  
 如同**工具選項**頁註冊上面所提的項目都有與分類的主索引鍵 \(`<PageCategory>`\) 的**工具選項**頁面和子機碼包含在網頁的子類別的名稱 \(`<PageSubcategory>`\)。  
  
 如果您使用受管理的套件架構時，使用<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>註冊類別提供**工具選項**頁面，然後設定<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A>屬性，以`true` ，表示資料頁支援自動化。  
  
 在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ 中找到的登錄項目*\<Version\>*\\AutomationProperties，其中 *\<Version\>* 版本的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]、 例如 8.0。  
  
> [!NOTE]
>  根路徑的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>* 可覆寫使用替代的根目錄時初始化 Visual Studio 命令介面時，如需詳細資訊，請參閱[命令列參數](../Topic/Command-Line%20Switches%20\(Visual%20Studio%20SDK\).md)。  
  
 下面，是結構的登錄項目：  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\> \\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 封裝 \= ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}'  
  
 Name \= '`<PageCategory>` .`<PageSubcategory>`'  
  
 'ProfileSave' \= 1\/0  
  
 下表列出的值低於 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties\\`<PageCategory>`。  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|自訂標準的類別名稱， **工具選項**頁面|機碼的名稱， `<PageCategory`\>，是正式非當地語系化名稱**工具選項**網頁類別\]。 **Note:**  支援自動化時，標準非當地語系化的分類和子類別名稱用來取得**工具選項**網頁的<xref:EnvDTE.Properties>集合。  如需詳細資訊，請參閱 [使用選項頁](../misc/using-options-pages.md)。 <br /><br /> 金鑰可以是空的或者也可以包含參考 ID 為實作的附屬 DLL 中當地語系化的字串。<br /><br /> 受管理的封裝架構中，為基礎的實作`<PageCategory`\> 您可以從取得`categoryName`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。|  
|ResourcePackage|REG\_SZ|GUID|選擇項。<br /><br /> 如果實作 VSPackage 未提供這些附屬 DLL 包含當地語系化字串。<br /><br /> 受管理的封裝架構會使用反映來取得正確的資源 VSPackage，所以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>並不會設定此引數。|  
  
 下表列出的值低於 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Version\>*\\AutomationProperties\\`<PageCategory>\<PageSubCategory>`。  
  
|名稱|型別|資料|描述|  
|--------|--------|--------|--------|  
|\(預設值\)|REG\_SZ|自訂子類別名稱**工具選項**頁面|機碼的名稱， `<PageSubCategory`\>，是正式非當地語系化名稱**工具選項**頁面子類別。 **Note:**  支援自動化時，標準非當地語系化的分類和子類別名稱用來取得**工具選項**網頁的<xref:EnvDTE.Properties>集合。  如需詳細資訊，請參閱 [使用選項頁](../misc/using-options-pages.md)。 <br /><br /> 金鑰可以是空的或者也可以包含參考 ID 為實作的附屬 DLL 中當地語系化的字串。<br /><br /> 受管理的封裝架構中，為基礎的實作`<PageSubCategory>`取自`pageName`引數，以<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式。|  
|封裝|REG\_SZ|GUID|GUID 的實作自訂的 VSPackage **工具選項**頁面。<br /><br /> 受管理的套件架構使用根據實作<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>使用反映來取得這個值。|  
|名稱|REG\_SZ|值為目前**工具選項**頁面 properties 集合|`<PageCategory>.<PageSubCategory>`字串，用來指稱**工具選項**頁面。  如需詳細資訊，請參閱 [使用選項頁](../misc/using-options-pages.md)。<br /><br /> 受管理的套件架構為基礎的實作，如從引數來取得名稱<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>建構函式的形式和`categoryName.pageName`。|  
|ProfileSave|DWORD|1\/0|選擇項。<br /><br /> 這個值會指示是否**工具選項**所儲存的頁面設定[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定機制，當使用者按一下**匯入\/匯出設定**命令**工具**功能表。<br /><br /> 如果機碼是否存在，且其值為 1，然後在**工具選項**網頁要求設定支援。<br /><br /> 如果受管理的套件架構為基礎的實作會設定這個值<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>提供給建構函式<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>屬性設定為 \[ `true`。|  
  
## 請參閱  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)   
 [使用選項頁](../misc/using-options-pages.md)   
 [使用 Interop 組件建立選項頁面](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [如何：建立自訂選項頁面](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [選項頁](../misc/options-pages.md)   
 [在選項頁面的自動化支援](../Topic/Automation%20Support%20for%20Options%20Pages.md)