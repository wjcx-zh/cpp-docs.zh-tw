---
title: "指定自訂建置工具 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
dev_langs: C++
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.assetid: e5161946-8002-418d-991e-219e6a8586f5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c65664e6c09028f1f15ded917a59ad013868f841
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-custom-build-tools"></a>指定自訂建置工具
A*自訂建置工具*提供建置系統必須建立特定的輸入的檔的資訊。 自訂建置工具指定要執行的命令，輸入檔案的清單，命令所產生的輸出檔案的清單和工具的選擇性描述。  
  
 如需自訂建置工具和自訂建置步驟的一般資訊，請參閱[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)。  
  
### <a name="to-specify-a-custom-build-tool"></a>若要指定自訂建置工具  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../ide/working-with-project-properties.md)。  
  
2.  按一下**組態屬性**啟用**組態**方塊。 在**組態**方塊中，選取您要指定自訂建置工具的組態。  
  
3.  在**方案總管 中**，選取自訂建置工具的輸入的檔。  
  
     如果**自訂建置工具**資料夾沒有出現，您所選取之檔案的副檔名是預設的工具相關聯。 例如，.c 和.cpp 檔案的預設工具是編譯器。 若要覆寫預設工具設定，在**組態屬性**節點，請在**一般**資料夾，請在**項目類型**屬性中，按一下**自訂建置工具**。 按一下**套用**和**自訂建置工具**節點顯示。  
  
4.  在**自訂建置工具**節點，請在**一般**資料夾中，指定與自訂相關聯的屬性建置工具：  
  
    -   在**其他相依性**，指定為其定義的自訂建置工具以外的任何其他檔案 （與自訂建置工具相關聯的檔案會隱含地視為工具的輸入）。 有其他輸入的檔不是自訂建置工具的需求。 如果您有一個以上的額外輸入，以分號隔開。  
  
         如果**其他相依性**檔案的日期晚於在輸入檔，然後再執行自訂建置工具。 如果要將所有的**其他相依性**檔案超過輸入檔中，而在輸入的檔是早於**輸出**屬性檔案中，然後自訂建置工具就不會執行。  
  
         例如，假設您有接受 MyInput.x 做為輸入，並產生 MyInput.cpp，和 MyInput.x 包含標頭檔，MyHeader.h 的自訂建置工具。 您可以指定 MyHeader.h 為 MyInput.x，輸入相依性和建置系統將會建置 MyInput.cpp 相對於 MyInput.x 或 MyHeader.h 過期時。  
  
         輸入相依性也可以確保您的自訂建置工具執行您所需的順序。 在上述範例中，假設 MyHeader.h 實際上自訂建置工具的輸出。 因為 MyHeader.h MyInput.x 的相依性，建置系統會先建置 Myheader.h MyInput.x 上執行自訂建置工具之前。  
  
    -   在**命令列**，如同您已指定它在命令提示字元中指定的命令。 指定有效的命令或批次檔和任何必要輸入或輸出檔案。 指定**呼叫**批次命令批次檔的名稱前面，保證會執行所有後續的命令。  
  
         可以使用 MSBuild 巨集以透過符號指定多個輸入和輸出檔案。 [!INCLUDE[crabout](../build/reference/includes/crabout_md.md)]指定檔案的位置或名稱的組檔案，請參閱[建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)。  
  
         因為 '%' 字元保留 MSBuild，如果您指定的環境變數取代每個 **%** 逸出字元與**%25**十六進位逸出序列。 例如，取代**%WINDIR%**與**%25WINDIR %25**。 MSBuild 會取代每個**%25**順序與 **%** 字元之前存取環境變數。  
  
    -   在**描述**，輸入此自訂建置工具的描述性訊息。 若要列印訊息**輸出**視窗時，建置系統以處理這項工具。  
  
    -   在**輸出**，指定輸出檔的名稱。 這是必要的項目。沒有這個屬性值，不會執行自訂建置工具。 如果自訂建置工具有一個以上的輸出，請使用分號分隔檔案名稱。  
  
         中指定輸出檔的名稱也應該是相同**命令列**屬性。 專案建置系統將會尋找檔案，並檢查它的日期。 如果輸出檔比輸入檔，或如果找不到輸出檔，就會執行自訂建置工具。 如果要將所有的**其他相依性**檔案超過輸入檔中，而在輸入的檔中指定的檔案小於**輸出**屬性，無法執行自訂建置工具。  
  
 如果您想要處理的自訂建置工具所產生的輸出檔的建置系統，您必須手動將它加入專案。 自訂建置工具會在建置期間更新的檔案。  
  
## <a name="example"></a>範例  
 假設您想要在專案中包含名為 parser.l 的檔案。 您想要處理以產生具有相同的基底名稱 (parser.c).c 檔 parser.l 用語彙分析器。  
  
 首先，您會將 parser.l 和 parser.c 加入至專案。 如果檔案尚不存在，您只要加入檔案的參考。 您建立 parser.l 的自訂建置工具，並輸入中的下列**命令**屬性：  
  
```  
lexer %(FullPath) .\%(Filename).c  
```  
  
 此命令會執行 parser.l 語彙分析器，並輸出 parser.c 到專案目錄。  
  
 在**輸出**屬性中，輸入下列命令：  
  
```  
.\%(Filename).c  
```  
  
 當您建置專案時，建置系統會比較 parser.l 和 parser.c 的時間戳記。 如果 parser.l 是較新，或如果不存在 parser.c，建置系統執行的值**命令列**屬性使 parser.c 最新狀態。 因為 parser.c 也已新增至專案，建置系統將會編譯 parser.c。  
  
## <a name="see-also"></a>另請參閱  
 [建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)   
 [為組建自訂進行疑難排解](../ide/troubleshooting-build-customizations.md)