---
title: 屬性頁 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.NotAProp.Edit
dev_langs:
- C++
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c24ed9328f77d26a8ad11a6ff6bdbf47bad9fbe3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381409"
---
# <a name="property-pages-visual-c"></a>屬性頁 (Visual C++)

藉由使用屬性頁，您可以指定 Visual Studio 專案的設定。 若要開啟 Visual Studio 專案的 [屬性頁] 對話方塊，請在 [專案] 功能表上，選擇 [屬性]。

您可以指定專案設定，使其套用所有組建組態，或是您可以為每個組建組態指定不同的專案屬性。 例如，您可以指定發行組態的特定設定和偵錯組態的其他設定。

並非所有可用的頁面都一定會顯示在 [屬性頁] 對話方塊中。 要顯示的網頁取決於專案中的檔案類型。

如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

若為非 Windows 專案，請參閱 [Linux C++ 屬性頁參考](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->。

## <a name="default-properties-vs-modified-properties"></a>預設屬性與修改的屬性的比較

當您使用 [新增專案] 對話方塊來建立專案時，Visual Studio 會使用指定的專案範本初始化專案屬性。 因此，在此範本中的屬性值可以視為該專案類型的預設值。 在其他專案類型中，屬性可能會有不同的預設值。

如果專案屬性值已修改，會顯示為粗體。 專案屬性可能會因為下列原因修改：

- 應用程式精靈變更了屬性，因為它需要的屬性值和專案範本中指定的不同。

- 您在 [新增專案] 對話方塊中指定不同的屬性值。

- 您在專案屬性頁上指定不同的屬性值。

> [!TIP]
> 若要查看 MSBuild 用來建置您專案的最後一組屬性值，請檢查前置處理器輸出檔，您可藉由使用下列命令列產生該檔案：**MSBuild /preprocess:** *preprocessor_output_filename*<sub>opt</sub> *project_filename*<sub>opt</sub>

## <a name="resetting-properties"></a>重設屬性

當您檢視專案的 [屬性頁] 對話方塊並在 [方案總管] 中選取專案節點時，您可以針對許多屬性選取 [從父代或專案預設值繼承] 或以另一種方式修改值。

當您檢視專案的 [屬性頁] 對話方塊並在 [方案總管] 中選取檔案時，您可以針對許多屬性選取 [從父代或專案預設值繼承] 或以另一種方式修改值。 不過，如果專案包含的許多檔案都具有和專案預設值不同的屬性值，建置專案需要較長的時間。

> [!TIP]
> 若要重新整理 [屬性頁] 對話方塊以顯示最新的選取內容，請選擇 [套用]。

大部分的專案預設值為系統 (平台) 預設值。 有些專案預設值衍生自樣式表，當您在專案的 [一般] 組態屬性頁的 [專案預設值] 區段中更新屬性時可套用這些樣式表。 如需詳細資訊，請參閱[一般屬性頁 (專案)](../ide/general-property-page-project.md)。

## <a name="specifying-user-defined-values"></a>指定使用者定義值

您必須定義特定屬性的值。 使用者定義值可以包含一或多個英數字元或專案檔巨集名稱。 其中某些屬性可以只取得一個使用者定義值，但是其他屬性可以取得以分號分隔的多個值清單。

若要指定屬性的使用者定義值，或是如果屬性可取得多個使用者定義值時指定清單，請在屬性名稱右邊的資料行中，執行下列其中一個動作：

- 輸入值或值的清單。

- 選擇下拉式箭頭。 如果可以使用 [編輯]，請選擇它，然後在文字方塊中鍵入值或值的清單。 指定清單的替代方式是在文字方塊中的個別行上輸入每個值。 在屬性頁上，這些值將顯示為以分號分隔的清單。

   若要插入專案檔巨集作為值，請選擇 [巨集]，然後按兩下巨集名稱。

- 選擇下拉式箭頭。 如果可以使用 [瀏覽]，請選擇它，然後選取一或多個值。

對於多重值屬性，當您選擇屬性名稱右欄中的下拉式箭頭，然後選擇 [編輯] 時，即可使用 [從父代或專案預設值繼承] 選項。 根據預設，這個選項已選取。

請注意，屬性頁只會為繼承自另一個層級之多重值屬性顯示目前層級的設定。 例如，如果在 [方案總管] 中選取檔案，而且您選取 C/C++ [前置處理器定義] 屬性，則會顯示檔案層級定義，但不會顯示繼承的專案層級定義。 若要檢視目前層級和繼承的值，請選擇屬性名稱右欄中的下拉式箭頭，然後選擇 [編輯]。 如果您使用 [Visual C++ 專案模型](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine)，這個行為也會影響檔案和專案上的物件。 也就是說，當您在檔案層級查詢屬性上的值，您不會在專案層級收到相同屬性的值。 您必須在專案層級明確取得屬性的值。 此外，屬性的某些繼承值可能來自無法以程式設計方式存取的樣式表。

## <a name="in-this-section"></a>本節內容

[進階、資訊清單工具、組態屬性、\<Projectname> 屬性頁對話方塊](../ide/advanced-manifest-tool.md)

[命令列屬性頁](../ide/command-line-property-pages.md)

[自訂建置步驟屬性頁：一般](../ide/custom-build-step-property-page-general.md)

[新增參考](../ide/adding-references-in-visual-cpp-projects.md)

[一般屬性頁 (檔案)](../ide/general-property-page-file.md)

[一般屬性頁面 (專案)](../ide/general-property-page-project.md)

[一般、資訊清單工具、組態屬性、\<Projectname> 屬性頁對話方塊](../ide/general-manifest-tool-configuration-properties.md)

[HLSL 屬性頁](../ide/hlsl-property-pages.md)

[HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)

[HLSL 屬性頁：一般](../ide/hlsl-property-pages-general.md)

[HLSL 屬性頁：輸出檔](../ide/hlsl-property-pages-output-files.md)

[輸入和輸出、資訊清單工具、組態屬性、\<Projectname> 屬性頁對話方塊](../ide/input-and-output-manifest-tool.md)

[隔離的 COM、資訊清單工具、組態屬性、\<Projectname> 屬性頁對話方塊](../ide/isolated-com-manifest-tool.md)

[連結器屬性頁](../ide/linker-property-pages.md)

[Managed 資源屬性頁](../ide/managed-resources-property-page.md)

[資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)

[MIDL 屬性頁](../ide/midl-property-pages.md)

[MIDL 屬性頁：進階](../ide/midl-property-pages-advanced.md)

[MIDL 屬性頁：一般](../ide/midl-property-pages-general.md)

[MIDL 屬性頁：輸出](../ide/midl-property-pages-output.md)

[NMake 屬性頁](../ide/nmake-property-page.md)

[資源屬性頁](../ide/resources-property-pages.md)

[VC++ 目錄屬性頁](../ide/vcpp-directories-property-page.md)

[Web 參考屬性頁](../ide/web-references-property-page.md)

[XML 資料產生器工具屬性頁](../ide/xml-data-generator-tool-property-page.md)

[XML 文件產生器工具屬性頁](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>另請參閱

[如何：建立和移除專案相依性](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br>
[如何：建立和編輯組態](/visualstudio/ide/how-to-create-and-edit-configurations)
