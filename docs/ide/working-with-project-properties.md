---
title: "使用專案屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
caps.latest.revision: "45"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de48e03c62d924334e005ffd7f008e0083fb405f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-project-properties"></a>使用專案屬性
在 ide 中建置專案所需的所有資訊會都公開為*屬性*。 此資訊包括應用程式名稱、 副檔名 （例如 DLL、 LIB、 EXE）、 編譯器選項、 連結器選項、 偵錯工具設定、 自訂建置步驟，以及許多其他項目。 通常，您會使用*屬性頁*(**專案 &#124;屬性**) 來檢視和修改這些屬性。 
  
 當您建立專案時，系統會指派各種屬性值。 預設值而稍有不同的類型而定的專案，以及哪些選項您應用程式精靈中選擇。 比方說，ATL 專案具有與 MIDL 檔相關的屬性，但這些不存在基本的主控台應用程式中。 在 屬性頁的 一般 窗格顯示的預設屬性：  
  
 ![Visual C# 43; &#43;專案預設值](../ide/media/visual-c---project-defaults.png "Visual c + + 專案預設值")  
  
 某些屬性，例如應用程式名稱、 套用至所有組建變化，不論目標平台或它是否偵錯或發行組建。 但大部分的屬性組態相關。 這是因為，編譯器必須知道特定平台執行程式，以及哪些特定的編譯器選項，以便產生正確的程式碼使用。 因此，當您設定屬性時，務必注意哪些組態與平台應該套用於新的值。 它只適用於偵錯 Win32 組建，或應該它也適用於偵錯 ARM 和 x64 的偵錯嗎？ 例如，**最佳化**屬性，根據預設，設定為**最大化的速度 (/ O2)**在發行組態中，但在偵錯組態停用。  
  
 屬性頁的設計可讓您永遠可以看到，以及如果視需要修改，哪些組態與平台屬性值應該會套用至。 下圖顯示在上方之清單方塊中的組態與平台資訊的屬性頁。 當**最佳化**屬性設定以下時，它只會套用到偵錯 Win32 組建中，這正好是使用中的組態，紅色的箭頭所示。  
  
 ![Visual C# 43; &#43;顯示使用中的組態屬性頁](../ide/media/visual-c---property-pages-showing-active-configuration.png "Visual c + + 屬性頁面顯示使用中的組態")  
  
 下圖顯示相同的專案屬性頁面中，但組態已變更為版本。 請注意不同屬性的值為最佳化。 也請注意，使用中的組態仍然偵錯。 您也可以設定任何設定的屬性。它沒有作用中的一個。  
  
 ![Visual C# 43; &#43;屬性頁面顯示發行組態](../ide/media/visual-c---property-pages-showing-release-config.png "Visual c + + 屬性頁面顯示發行組態")  
  
 專案系統本身根據 MSBuild，定義檔案格式和建置專案的任何類型的規則。 MSBuild 會管理的多個組態與平台，建置的複雜性，但是您需要更了解其運作方式。 這是特別重要，如果您想要定義自訂的設定或建立可重複使用的屬性，您可以共用，匯入多個專案集合。  
  
 專案屬性會儲存在專案檔 (*.vcxproj) 中直接或其他.xml 或.props 檔案中的專案檔案匯入和其提供的預設值。 如先前所示，在相同組態的相同屬性可能會指派不同的檔案不同的值。 當您建置專案時，MSBuild 引擎會評估專案檔與所有匯入的檔案，以妥善定義的順序 （如下所述）。 評估每個檔案時，任何在該檔案中定義的屬性值將會覆寫現有的值。 未指定任何值被繼承自稍早所評估的檔案。 因此，當您設定屬性與屬性頁，務必也要注意，您設定。 如果在.props 檔案中，"X"設定屬性，但此屬性設定為"Y"專案檔中，專案將建置屬性設定為"Y"。 如果"Z"的專案項目上設定相同屬性，例如.cpp 檔，MSBuild 引擎會使用"Z"值。 如需詳細資訊，請參閱[屬性繼承](#bkmkPropertyInheritance)本文稍後。  
  
## <a name="build-configurations"></a>組建組態  
 組態是只任意群組的名稱的屬性。 Visual Studio 提供偵錯和發行組態，與每個設定適當的偵錯組建或發行組建的各種屬性。 您可以使用**Configuration Manager**自訂組態定義為組建的特定類別的群組屬性的便利方式。 屬性管理員用於進階處理屬性，但是我們將它引入以下因為它可協助視覺化的屬性組態。 您可以存取它從**檢視 &#124; 屬性管理員**或**檢視 &#124;其他視窗 &#124;屬性管理員**根據您的設定。 它包含專案中的每個組態/平台組節點。 每個這些節點是節點設定該組態的一些特定屬性的屬性工作表 （.props 檔案）。  
  
 ![屬性管理員](../ide/media/property-manager.png "屬性管理員")  
  
 如果您移至 （請參閱圖） 的屬性頁中 [一般] 窗格並將字元集屬性設定為 「 未設定 」 而非 「 使用 Unicode 」，然後按一下**確定**，[屬性管理員] 會顯示任何**Unicode 支援**屬性工作表目前的設定，但它仍會有其他設定。  
  
 如需屬性管理員 」 和 「 屬性工作表的詳細資訊，請參閱[建立可重複使用的屬性設定](#bkmkPropertySheets)本文稍後。  
  
> [!TIP]
>  .User 檔案是舊版的功能，而且我們建議您將它刪除以保持組態/平台根據正確分組的屬性。  
  
## <a name="target-platforms"></a>目標平台  
 *目標平台*指的裝置和/或可執行檔將在執行的作業系統類型。 您可以建立多個平台的專案。 C + + 專案可用的目標平台相依於專案; 類型它們包括但不限於使用 Win32、 x64、 ARM、 Android 和 iOS。     **X86**目標平台，您可能會看到在**Configuration Manager**等同於**Win32**原生 c + + 專案中。 Win32 表示 32 位元 Windows 和**x64**表示 64 位元 Windows。 如需這兩個平台的詳細資訊，請參閱[執行 32 位元應用程式](https://msdn.microsoft.com/library/windows/desktop/aa384249\(v=vs.85\).aspx)。  
  
 **任何 CPU**目標平台值中，您可能會看到**Configuration Manager**具有原生 c + + 專案; 不會影響與 C + CLI 和其他.NET 專案類型。 如需詳細資訊，請參閱 [/CLRIMAGETYPE (指定 CLR 映像類型)](../build/reference/clrimagetype-specify-type-of-clr-image.md)。  
  
## <a name="property-pages"></a>「屬性頁」  
 如同稍早所述，Visual c + + 專案系統會根據[MSBuild](/visualstudio/msbuild/msbuild-properties)值會儲存在 XML 專案檔中，預設.props 和.targets 檔案。 Visual Studio 2015 中，這些檔案會放在**\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**。 Visual Studio 2017，這些檔案會放在 **\\Program Files (x86)\\Microsoft Visual Studio\\2017年\\_edition_\\Common7\\IDE\\VC\\VCTargets**，其中_edition_已安裝的 Visual Studio 版本。 屬性也會儲存任何自訂的.props 檔案，您可能會加入您自己的專案中。 我們強烈建議您無法手動編輯這些檔案，並改為在 IDE 中使用屬性頁來修改所有屬性，特別是那些參與繼承，除非您有非常深入了解 MSBuild。  
  
 下圖顯示 Visual C++ 專案的屬性頁。 在左窗格中， **VC + + 目錄***規則*選取時，和右窗格會列出與該規則相關聯的屬性。 `$(...)`值不幸的是稱為*巨集*。 這些是*不*C/c + + 巨集，但只需編譯時間常數。 中會討論的巨集[屬性頁面巨集](#bkmkPropertiesVersusMacros)本文中稍後的一節。)  
  
 ![專案屬性頁](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")  
  
> [!WARNING]
>  **通用屬性**舊版 Visual Studio 中的組態已遭到移除。 若要加入至專案的參考，您現在使用**加入參考**一樣 managed 語言中的對話方塊。 請參閱[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)。  
  
#### <a name="to-set-a-property-for-a-project"></a>若要設定專案的屬性  
  
1.  大部分情況下，您可以在專案層級設定屬性而不需要建立自訂的屬性工作表。 在主功能表上選擇 [**專案 &#124;屬性**，或以滑鼠右鍵按一下專案節點中**方案總管] 中**選擇**屬性**。  
  
2.  使用**組態**和**平台**清單來指定應該套用變更的屬性群組 對話方塊頂端的方塊。 在許多情況下**所有平台**和**所有組態**是正確的選擇。 若要設定一些組態，多重選取的屬性中**屬性管理員**，然後開啟捷徑功能表並選擇 **屬性**。  
  
 **屬性頁**對話方塊顯示只套用至目前專案的屬性頁。 例如，如果專案沒有 .idl 檔案，就不會顯示 MIDL 屬性頁。  
  
 當您反白顯示屬性頁中的屬性時，您可以按**F1**移至對應的編譯器或連結器選項的詳細資訊的參考主題。  
  
 您可以在這些主題中找到每個屬性頁的詳細資訊：  
  
-   [一般屬性頁面 (專案)](../ide/general-property-page-project.md)  
  
-   [一般屬性頁 (檔案)](../ide/general-property-page-file.md)  
  
-   [命令列屬性頁](../ide/command-line-property-pages.md)  
  
-   [C++ 偵錯組態的專案設定](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)  
  
-   [NMake 屬性頁](../ide/nmake-property-page.md)  
  
-   [連結器屬性頁](../ide/linker-property-pages.md)  
  
-   [資源屬性頁](../ide/resources-property-pages.md)  
  
-   [MIDL 屬性頁](../ide/midl-property-pages.md)  
  
-   [Web 參考屬性頁](../ide/web-references-property-page.md)  
  
-   [XML 資料產生器工具屬性頁](../ide/xml-data-generator-tool-property-page.md)  
  
## <a name="to-quickly-browse-and-search-all-properties"></a>若要快速瀏覽和搜尋所有的屬性  
 **所有選項**屬性頁 (下**組態屬性 &#124;C/C++**節點**屬性頁**對話方塊) 可快速瀏覽和搜尋目前內容中可用的屬性。 其中有特別的搜尋方塊和協助篩選結果的簡單語法：  
  
 沒有前置詞：  
 只在屬性名稱中搜尋 (不區分大小寫的子字串)。  
  
 '/' 或 '-'：  
 只在編譯器參數中搜尋 (不區分大小寫的前置詞)  
  
 v:  
 只在值中搜尋 (不區分大小寫的子字串)。  
  
##  <a name="bkmkPropertiesVersusMacros"></a>屬性頁巨集  
 A*巨集*是一個編譯時間常數，可以參考由 Visual Studio 或 MSBuild 系統所定義的值或使用者定義的值。 藉由使用巨集而不使用硬式編碼值 (例如目錄路徑)，您可以更輕鬆地在電腦之間以及在 Visual Studio 版本之間共用屬性設定，並且更能確保您的專案設定正確參與屬性繼承。 您可以使用屬性編輯器來檢視所有可用的巨集的值。  
  
### <a name="predefined-macros"></a>預先定義巨集  
 全域巨集  
 套用至專案組態中的所有項目。 具有語法 `$(name)`。 例如，`$(VCInstallDir)` 即是全域巨集，這會儲存 Visual Studio 安裝根目錄。 全域巨集對應於 MSBuild 中的 `PropertyGroup`。  
  
 項目巨集  
 具有語法 `%(name)`。 對於檔案，項目巨集只套用至該檔案。例如，您可以使用 `%(AdditionalIncludeDirectories)` 來指定只套用至特定檔案的 Include 目錄。 這類型的項目巨集對應於 MSBuild 中的 `ItemGroup` 中繼資料。 在專案組態的內容中使用時，項目巨集會套用至特定類型的所有檔案。 例如，C/c + +**前置處理器定義**組態屬性可以接受`%(PreprocessorDefinitions)`套用至專案中所有.cpp 檔案的項目巨集。 這類型的項目巨集對應於 MSBuild 中的 `ItemDefinitionGroup` 中繼資料。 如需詳細資訊，請參閱[項目定義](/visualstudio/msbuild/item-definitions)。  
  
### <a name="user-defined-macros"></a>使用者定義巨集  
 您可以建立*使用者定義巨集*来做為專案建置中的變數。 例如，您可以建立使用者定義巨集，提供自訂建置步驟或自訂建置工具的值。 使用者定義巨集是名稱/值組。 在專案檔中，使用**$(***名稱***)**標記法來存取值。  
  
 使用者定義巨集會儲存在屬性工作表中。 如果您的專案尚未包含的屬性工作表，您可以建立一個依照底下步驟[建立可重複使用的屬性設定](#bkmkPropertySheets)。  
  
##### <a name="to-create-a-user-defined-macro"></a>建立使用者定義巨集  
  
1.  在**屬性管理員**視窗 (在功能表列上選擇 **檢視**，**屬性管理員**)，開啟屬性工作表 （其名稱以.user 結束） 的捷徑功能表，然後選擇屬性。 **屬性頁**該屬性工作表 對話方塊隨即開啟。  
  
2.  在對話方塊的左窗格中，選取**使用者巨集**。 在右窗格中，選擇 **加入巨集** 按鈕以開啟**加入使用者巨集** 對話方塊。  
  
3.  在對話方塊中，指定巨集的名稱和值。 （選擇性） 選取**設定此巨集做為建置環境中的環境變數**核取方塊。  
  
## <a name="property-editor"></a>屬性編輯器  
 您可以使用屬性編輯器，修改特定字串屬性和選擇巨集做為值。 若要存取屬性編輯器，請選取屬性頁上的屬性，然後選擇右邊的向下箭號按鈕。 如果下拉式清單包含**\<編輯 >**，您可以選擇來顯示該屬性的屬性編輯器。  
  
 ![屬性 &#95;編輯器 &#95; 下拉式清單中](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")  
  
 在 [屬性編輯器] 中，您可以選擇**巨集**按鈕，以檢視可用巨集及其目前值。 下圖顯示屬性編輯器**其他 Include 目錄**屬性之後**巨集**選擇按鈕。 當**從父代或專案預設值繼承**核取方塊已選取並加入新的值，會附加至目前繼承任何值。 如果您清除此核取方塊，則新值會取代繼承的值。 在大部分情況下，讓核取方塊保持已選取狀態。  
  
 ![屬性編輯器中，Visual C# 43; &#43;] (../ide/media/propertyeditorvc.png "PropertyEditorVC")  
  
##  <a name="bkmkPropertySheets"></a>建立可重複使用的屬性設定  
 雖然可以按照每個使用者、每台電腦基準設定「全域」屬性，但是我們已不建議使用。 相反地，我們建議您改用**屬性管理員**建立*屬性工作表*以儲存設定的每一種您想要能夠重複使用或與他人共用的專案。 屬性工作表也會減少不慎變更其他專案類型之屬性設定的可能性。 屬性工作表會詳細討論[建立可重複使用的屬性設定](#bkmkPropertySheets)。  
  
> [!IMPORTANT]
>  **.user 檔案，以及為什麼會有問題**  
>   
>  Visual Studio 的過去版本會使用具有.user 副檔名且位於的全域屬性工作表\<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ 資料夾。 我們已不建議使用，因為這些檔案是按照每位使用者、每台電腦基準來設定專案組態的屬性。 這類「全域」設定可能干擾組建，尤其是在您以組建電腦上的多個平台為目標時。 例如，如果您同時有 MFC 專案和 Windows Phone 專案，那麼 .user 屬性對其中一個專案會是無效的。 可重複使用的屬性工作表具有較大彈性且更為穩固。  
>   
>  雖然 .user 檔案仍舊由 Visual Studio 安裝並且參與屬性繼承，但預設為空白。 最佳做法是刪除其參考中的**屬性管理員**為了確保您的專案運作獨立於任何每位使用者，每個電腦設定務必確保在 SCC （原始程式碼中的正確行為控制） 環境。  
  
 若要顯示**屬性管理員**，在功能表列上選擇 **檢視**，**其他視窗**，**屬性管理員**。  
  
 如果您有一常用組您想要套用至多個專案的屬性，您可以使用**屬性管理員**可重複使用的擷取它們*屬性工作表*檔案，其依慣例有.props 檔案的副檔名。 您可以將一個或多個工作表套用至新的專案，這樣就不需要從頭設定其屬性。 若要存取**屬性管理員**，在功能表列上選擇 **檢視**，**屬性管理員**。  
  
 ![屬性管理員捷徑功能表](../ide/media/sharingnew.png "SharingNew")  
  
 每個組態節點下，您會看到該組態適用於每一個屬性工作表的節點。 系統會新增設定值，當您建立專案的應用程式精靈中選擇的選項為基礎的屬性工作表。 以滑鼠右鍵按一下任何節點，然後選擇屬性，以查看套用到該節點的屬性。 所有屬性工作表會自動匯入專案的 「 主要 」 的屬性工作表 (ms.cpp.props)，並會出現在 [屬性管理員] 中的順序進行評估。 您可以移動它們以變更評估順序。 稍後會評估的屬性工作表，將會覆寫之前評估工作表中的值。  
  
 如果您選擇**加入新的專案屬性工作表**，然後選取，例如 MyProps.props 屬性工作表，屬性頁 對話方塊隨即出現。 請注意，這會套用至 MyProps 屬性工作表。您所做的任何變更都將寫入至工作表，而非專案檔 (.vcxproj)。  
  
 如果直接在 .vcxproj 檔案中設定相同屬性，就會覆寫屬性工作表中的屬性。  
  
 您可以視需要匯入屬性工作表。 方案中的多個專案可以繼承同一個屬性工作表中的設定，而且專案可以有多個工作表。 屬性工作表本身可以繼承另一個屬性工作表中的設定。  
  
 您也可以為多個組態建立一個屬性工作表。 若要這樣做，請建立每個組態的屬性工作表，其中一個開啟的捷徑功能表，選擇**加入現有屬性工作表**，然後再加入其他工作表。 不過，如果您使用一個通用屬性工作表，請注意當您設定屬性時，這個屬性是針對工作表所套用至的所有組態來設定；還要知道 IDE 不會告訴您哪些專案或其他屬性工作表是繼承自指定的屬性工作表。  
  
 在具有許多個專案的大型方案中，建立方案層級的屬性工作表會很有用。 當您將專案加入方案時，使用**屬性管理員**將該屬性工作表加入至專案。 如果這必須在專案層級進行，您可以加入新的屬性工作表來設定專案特定值。  
  
> [!IMPORTANT]
>  由於 .props 檔案不是建立做為專案項目，因此預設不參與原始檔控制。 如果要在原始檔控制中包含這個檔案，可以手動將其加入做為方案項目。  
  
#### <a name="to-create-a-property-sheet"></a>建立屬性工作表  
  
1.  在功能表列上選擇 **檢視**，**屬性管理員**。 **屬性管理員**隨即開啟。  
  
2.  若要定義屬性工作表的範圍，請選取套用的項目。 這可以是特定組態，或其他屬性工作表。 開啟這個項目的捷徑功能表，然後選擇**加入新的專案屬性工作表**。 指定名稱和位置。  
  
3.  在**屬性管理員**，開啟新的屬性工作表，然後設定您想要包含的屬性。  
  
##  <a name="bkmkPropertyInheritance"></a>屬性繼承  
 專案屬性是有層次的。 每一層都會繼承上一層的值，但是繼承的值可以藉由明確設定屬性來覆寫。 以下是基本繼承樹狀：  
  
1.  MSBuild CPP Toolset 的預設設定 (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props，由 .vcxproj 檔案匯入)。  
  
2.  屬性工作表  
  
3.  .vcxproj 檔案  (可以覆寫預設及屬性工作表設定)。  
  
4.  項目中繼資料  
  
> [!TIP]
>  在屬性頁中的屬性`bold`定義在目前內容中。 以一般字型表示的屬性是繼承的。  
  
 專案檔 (.vcxproj) 會在建置階段匯入其他屬性工作表。 匯入所有屬性工作表之後，將會對專案檔進行評估，任何屬性值的最後一個定義就是使用的值。 有時候，檢視展開的檔案以判斷指定的屬性值如何繼承，十分有用。 若要檢視展開的版本，請在 Visual Studio 命令提示字元輸入下列命令  (將預留位置檔案名稱變更為您要使用的名稱)。  
  
 **msbuild /pp:** *temp* **.txt** *myapp* **.vcxproj**  
  
 除非您熟悉 MSBuild，不然展開的專案檔可能很龐大，而且難以了解。 以下是專案檔的基本結構：  
  
1.  基本專案屬性，IDE 不會公開這些屬性。  
  
2.  匯入 Microsoft.cpp.default.props，這會定義一些與工具組無關的基本屬性。  
  
3.  全域組態屬性 (公開為**PlatformToolset**和**專案**預設屬性上**組態一般**頁面。 這些屬性會決定 Microsoft.cpp.props 在下一個步驟中匯入哪些工具組和內建屬性工作表。  
  
4.  匯入 Microsoft.cpp.props，這會設定大部分的專案預設值。  
  
5.  匯入所有屬性工作表，包括 .user 檔案。 這些屬性工作表可以覆寫以外的所有內容**PlatformToolset**和**專案**預設屬性。  
  
6.  剩餘的專案組態屬性。 這些值可以覆寫屬性工作表上已設定的屬性。  
  
7.  項目 (檔案) 以及其中繼資料。 這些項目永遠握有 MSBuild 評估規則的最後決定權，即使是在其他屬性和匯入之前出現。  
  
 如需詳細資訊，請參閱 [MSBuild 屬性](/visualstudio/msbuild/msbuild-properties)。  
  
## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>將 Include 目錄加入至一組預設目錄  
 當您將 Include 目錄加入至專案時，注意不要覆寫所有的預設目錄。 正確加入目錄的方式是附加新路徑，例如"C:\MyNewIncludeDir\"，然後將附加**$ （includepath)**巨集的屬性值。  
  
## <a name="setting-environment-variables-for-a-build"></a>設定組建的環境變數  
 Visual C++ 編譯器 (cl.exe) 會辨識某些環境變數，特別是 LIB、LIBPATH、PATH 和 INCLUDE。 當您使用在 IDE 中的屬性中設定的建置[VC + + 目錄屬性頁](../ide/vcpp-directories-property-page.md)屬性頁用來設定這些環境變數。 如果已經設定 LIB、LIBPATH 和 INCLUDE 值 (例如，透過開發人員命令提示字元)，這些值會取代為對應 MSBuild 屬性的值。 組建接著會在 PATH 之前加上 [VC++ 目錄] 可執行檔目錄屬性的值。 您可以設定使用者定義的環境變數建立的使用者定義巨集，然後核取方塊，指出**設定此巨集做為建置環境中的環境變數**。  
  
## <a name="setting-environment-variables-for-a-debugging-session"></a>設定偵錯工作階段的環境變數  
 專案的左窗格中**屬性頁**對話方塊方塊中，展開 **組態屬性**，然後選取 **偵錯**。 
  
 在右窗格中，修改**環境**或**合併環境**專案設定，然後選擇 [**確定**] 按鈕。  

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>修改屬性和目標，而不會變更專案檔
您可以覆寫專案屬性和目標從 MSBuild 命令提示字元，而不會變更專案檔。 當您想要套用某些屬性，暫時或偶爾，這非常有用。 它會假設 MSBuild 的一些知識。 如需詳細資訊，請參閱[MSBUild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild)。

> [!IMPORTANT]
> 您可以使用 Visual Studio 或任何文字編輯器中的 XML 編輯器來建立.props 或.targets 檔案。 請勿使用**屬性管理員**在此案例因為它會將屬性加入至專案檔。

*若要覆寫專案屬性：*
- 建立.props 檔案，指定您想要覆寫的屬性。 
- 從命令提示字元： 設定 ForceImportBeforeCppTargets="C:\sources\my_props.props"
 
*若要覆寫專案的目標：*
1) 建立與其實作或特定目標的.targets 檔案
2) 從命令提示字元： 設定 ForceImportAfterCppTargets ="C:\sources\my_target.targets"
 
您也可以使用 /p： 選項，以設定 msbuild 命令列上的其中一個選項：

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props" 
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets" 
```  

覆寫屬性和目標以這種方式相當於下列 imports 加入方案中的所有.vcxproj 檔案：

```cmd 
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```  

## <a name="see-also"></a>請參閱  
 [建立和管理 Visual c + + 專案](../ide/creating-and-managing-visual-cpp-projects.md) [.vcxproj 和.props 檔案結構](vcxproj-file-structure.md)[屬性頁的 XML 檔案](property-page-xml-files.md)