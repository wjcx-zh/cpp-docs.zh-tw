---
title: 如何： 將自訂建置工具加入至 MSBuild 專案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msbuild.cpp.howto.addcustombuildtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efa484e4ad57a3a1f27621e16dddcf90135b7057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>如何：將自訂建置工具加入至 MSBuild 專案
自訂建置工具是與特定檔案相關聯的使用者定義的命令列工具。  
  
 針對特定的檔案，指定在專案檔 (.vcxproj) 命令列執行、 任何其他輸入或輸出檔案，以及要顯示的訊息。 如果**MSBuild**判斷的輸出檔會與您的輸入檔過期，它會顯示訊息，並執行命令列工具。  
  
 若要指定自訂建置工具執行時，請使用其中一個或多個`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`專案檔中的 XML 項目。 例如，您可以指定自訂建置工具執行之後 MIDL 編譯器和 C/c + + 編譯器之前。 指定`CustomBuildBeforeTargets`執行工具，才可以執行特定目標; 的項目`CustomBuildAfterTargets`在特定的目標; 後執行此工具的項目或執行兩個目標之間執行工具這兩個項目。 如果指定兩項目，則您的自訂建置工具執行在其預設位置，這是之前**MIDL**目標。  
  
 自訂建置步驟和自訂建置工具共用指定的資訊`CustomBuildBeforeTargets`和`CustomBuildAfterTargets`XML 項目。 在您的專案檔中指定這些目標一次。  
  
### <a name="to-add-a-custom-build-tool"></a>若要加入自訂建置工具  
  
1.  將項目群組加入至專案檔，並將每個輸入檔案項目。 指定命令、 其他輸入、 輸出和訊息做為項目中繼資料，如下所示。 這個範例假設 「 faq.txt"檔案存在於與您的專案相同的目錄。  
  
    ```  
    <ItemGroup>  
      <CustomBuild Include="faq.txt">  
        <Message>Copying readme...</Message>  
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>  
        <Outputs>$(OutDir)%(Identity)</Outputs>  
      </CustomBuild>  
    </ItemGroup>  
    ```  
  
### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>若要定義組建中的自訂建置工具會執行位置  
  
1.  下列的屬性群組加入至專案檔。 您必須指定至少其中一個目標，但如果您只想要讓您執行之前 （或之後） 的建置步驟省略其他特定的目標。 這個範例會在編譯之後，但連結之前，執行自訂步驟。  
  
    ```  
    <PropertyGroup>  
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>  
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>  
    </PropertyGroup>  
    ```  
  
## <a name="see-also"></a>請參閱  
 [逐步解說： 使用 MSBuild 來建立 Visual c + + 專案](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)   
 [如何： 在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)   
 [如何：將自訂建置步驟新增至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)