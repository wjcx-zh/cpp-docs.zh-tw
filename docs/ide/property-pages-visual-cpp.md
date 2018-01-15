---
title: "屬性頁 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.NotAProp.Edit
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0c342148266dff9551d2705f8095250daf2b096
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="property-pages-visual-c"></a>屬性頁 (Visual C++)

藉由使用屬性頁，您可以指定 Visual Studio 專案的設定。 若要開啟**屬性頁**對話方塊 for Visual Studio 專案中，在**專案**功能表上，選擇**屬性**。

您可以指定專案設定，使其套用所有組建組態，或是您可以為每個組建組態指定不同的專案屬性。 例如，您可以指定發行組態的特定設定和偵錯組態的其他設定。

並非所有可用的頁面都一定會顯示在**屬性頁** 對話方塊。 要顯示的網頁取決於專案中的檔案類型。

如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

對於非 Windows 的專案，請參閱[Linux c + + 屬性頁面參考](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->。

## <a name="default-properties-vs-modified-properties"></a>預設屬性與修改的屬性的比較

當您使用**新專案**對話方塊來建立專案時，Visual Studio 會使用指定的專案範本初始化專案屬性。 因此，在此範本中的屬性值可以視為該專案類型的預設值。 在其他專案類型中，屬性可能會有不同的預設值。

如果專案屬性值已修改，會顯示為粗體。 專案屬性可能會因為下列原因修改：

- 應用程式精靈變更了屬性，因為它需要的屬性值和專案範本中指定的不同。

- 您指定不同的屬性值中**新專案** 對話方塊。

- 您在專案屬性頁上指定不同的屬性值。

> [!TIP]
> 若要查看 MSBuild 用來建置您的專案的屬性值的最終集合，檢查您可藉由使用此命令列產生的前置處理器輸出檔案： **MSBuild / 前置處理：** *preprocessor_output_檔名*<sub>選擇</sub> *project_filename*<sub>選擇加入</sub>

## <a name="resetting-properties"></a>重設屬性

當您檢視**屬性頁**專案和專案節點的對話方塊中選取**方案總管 中**，對於許多屬性，您可以選取**繼承自父代或專案預設值**修改的值或另一種方式。

當您檢視**屬性頁**專案和檔案 對話方塊中選取**方案總管 中**，對於許多屬性，您可以選取**繼承自父代或專案預設值**修改的值或另一種方式。 不過，如果專案包含的許多檔案都具有和專案預設值不同的屬性值，建置專案需要較長的時間。

> [!TIP]
> 若要重新整理**屬性頁**對話方塊中，使其顯示最新的選取項目，選擇**套用**。

大部分的專案預設值為系統 (平台) 預設值。 有些專案預設值是衍生自更新中的屬性時，所套用的樣式表**專案預設**區段**一般**專案的組態屬性頁。 如需詳細資訊，請參閱[一般屬性頁 （專案）](../ide/general-property-page-project.md)。

## <a name="specifying-user-defined-values"></a>指定使用者定義值

您必須定義特定屬性的值。 使用者定義值可以包含一或多個英數字元或專案檔巨集名稱。 其中某些屬性可以只取得一個使用者定義值，但是其他屬性可以取得以分號分隔的多個值清單。

若要指定屬性的使用者定義值，或是如果屬性可取得多個使用者定義值時指定清單，請在屬性名稱右邊的資料行中，執行下列其中一個動作：

- 輸入值或值的清單。

- 選擇下拉式箭號。 如果**編輯**可用，選擇該連結，然後在文字方塊中，輸入值的清單。 指定清單的替代方式是在文字方塊中的個別行上輸入每個值。 在屬性頁上，這些值將顯示為以分號分隔的清單。

   若要插入專案檔巨集做為值，請選擇**巨集**，然後按兩下巨集名稱。

- 選擇下拉式箭號。 如果**瀏覽**可用，選擇它，然後選取一個或多個值。

對於多重值屬性，**繼承自父代或專案預設值**選項時，使用您選擇要在屬性名稱右邊資料行中的下拉箭號，然後選擇**編輯**。 根據預設，這個選項已選取。

請注意，屬性頁只會為繼承自另一個層級之多重值屬性顯示目前層級的設定。 比方說，如果在 [選取檔案**方案總管] 中**，而且您選取 C/c + +**前置處理器定義**屬性，會顯示檔案層級定義，但是繼承專案層級定義不會顯示。 若要檢視目前層級和繼承的值，選擇要在屬性名稱右邊資料行中的下拉箭號，然後選擇**編輯**。 如果您使用[Visual c + + 專案模型](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine)，這個行為也會影響物件的檔案和專案。 也就是說，當您在檔案層級查詢屬性上的值，您不會在專案層級收到相同屬性的值。 您必須在專案層級明確取得屬性的值。 此外，屬性的某些繼承值可能來自無法以程式設計方式存取的樣式表。

## <a name="in-this-section"></a>本節內容

[進階、 資訊清單工具、 組態屬性、\<專案名稱 > 屬性頁對話方塊](../ide/advanced-manifest-tool.md)

[命令列屬性頁](../ide/command-line-property-pages.md)

[自訂建置步驟屬性頁：一般](../ide/custom-build-step-property-page-general.md)

[加入參考](../ide/adding-references-in-visual-cpp-projects.md)

[一般屬性頁 (檔案)](../ide/general-property-page-file.md)

[一般屬性頁面 (專案)](../ide/general-property-page-project.md)

[一般、 資訊清單工具、 組態屬性、\<專案名稱 > 屬性頁對話方塊](../ide/general-manifest-tool-configuration-properties.md)

[HLSL 屬性頁](../ide/hlsl-property-pages.md)

[HLSL 屬性頁：進階](../ide/hlsl-property-pages-advanced.md)

[HLSL 屬性頁：一般](../ide/hlsl-property-pages-general.md)

[HLSL 屬性頁：輸出檔](../ide/hlsl-property-pages-output-files.md)

[輸入和輸出、 資訊清單工具、 組態屬性、\<專案名稱 > 屬性頁對話方塊](../ide/input-and-output-manifest-tool.md)

[隔離的 COM、 資訊清單工具、 組態屬性、\<專案名稱 > 屬性頁對話方塊](../ide/isolated-com-manifest-tool.md)

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

[如何：建立和移除專案相依性](/visualstudio/ide/how-to-create-and-remove-project-dependencies)  
[如何：建立和編輯組態](/visualstudio/ide/how-to-create-and-edit-configurations)  
