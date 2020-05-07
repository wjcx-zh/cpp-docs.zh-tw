---
title: 指定自訂建置工具
ms.date: 06/05/2018
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
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: dbce226b34503a9e8e70b6f19d9aa0c68ef487f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314750"
---
# <a name="specify-custom-build-tools"></a>指定自訂建置事件

「自訂建置工具」** 提供建置系統建置特定輸入檔所需的資訊。 自訂建置工具指定要執行的命令、輸入檔清單、命令所產生的輸出檔清單及工具的選擇性描述。

如需自訂建置工具和自訂建置步驟的一般資訊，請參閱[了解自訂建置步驟和建置事件](understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-custom-build-tool"></a>指定自訂建置工具

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](working-with-project-properties.md)。

1. 選擇 [組態屬性]**** 以啟用 [組態]**** 方塊。 在 [組態]**** 方塊中，選取您要指定自訂建置工具的組態。

1. 在 [方案總管]**** 中，選取自訂建置工具的輸入檔。

   如果 [自訂建置工具]**** 資料夾未顯示，您所選取之檔案的副檔名已與預設工具建立關聯。 例如，.c 和 .cpp 檔案的預設工具是編譯器。 若要覆寫預設工具設定，請在 [組態屬性]**** 節點之 [一般]**** 資料夾的 [項目類型]**** 屬性中，選擇 [自訂建置工具]****。 選擇 [套用]****，[自訂建置工具]**** 節點即會顯示。

1. 在 [自訂建置工具]**** 節點的 [一般]**** 資料夾中，指定與自訂建置工具建立關聯的屬性：

   - 在 [其他相依性]**** 中，指定為其定義自訂建置工具以外的任何其他檔案 (與自訂建置工具建立關聯的檔案會隱含視為工具的輸入)。 自訂建置工具不一定要有其他輸入檔。 如果您有一個以上的額外輸入，請以分號分隔。

      如果**其他相依性**檔案的日期晚於輸入檔，則會執行自訂建置工具。 如果所有**其他相依性**檔案都早於輸入檔，且輸入檔早於**輸出**屬性檔，則不會執行自訂建置工具。

      例如，假設您有自訂建置工具，接受 MyInput.x 作為輸入並產生 MyInput.cpp，且該 MyInput.x 包含標頭檔 MyHeader.h。 您可以指定 MyHeader.h 作為 MyInput.x 的輸入相依性，建置系統將會根據 MyInput.x 或 MyHeader.h 建置過時的 MyInput.cpp。

      輸入相依性也可確保您的自訂建置工具依您所需的順序執行。 在上述範例中，假設 MyHeader.h 實際上是自訂建置工具的輸出。 由於 MyHeader.h 是 MyInput.x 的相依性，建置系統會先建置 Myheader.h，再於 MyInput.x 上執行自訂建置工具。

   - 在 [命令列]**** 中指定命令，就像是在命令提示字元中指定一樣。 指定有效的命令或批次檔，以及任何必要的輸入或輸出檔。 在批次檔的名稱前面指定**呼叫**批次命令，以保證所有後續命令都會執行。

      您可以使用 MSBuild 巨集透過符號指定多個輸入和輸出檔。 如需有關如何指定檔案位置或檔案集名稱的資訊，請參閱[組建命令和屬性的一般宏](reference/common-macros-for-build-commands-and-properties.md)。

      因為 '% ' 字元是由 MSBuild 保留，所以如果您指定環境變數，請將**%** 每個逸出字元取代為 **%25**個十六進位的逸出序列。 例如，以 **%25WINDIR%25** 取代 **%WINDIR%**。 MSBuild 會在存取環境變數之前，以 **%** 字元取代每個 **%25** 序列。

   - 在 [描述]**** 中，輸入此自訂建置工具的描述性訊息。 當建置系統處理此工具時，會將訊息列印至 [輸出]**** 視窗。

   - 在 [輸出]**** 中，指定輸出檔的名稱。 這是必要項目；如果沒有這個屬性的值，則不會執行自訂建置工具。 如果自訂建置工具有一個以上的輸出，請以分號分隔檔案名稱。

      輸出檔的名稱應該與 [命令列]**** 屬性中指定的名稱相同。 專案建置系統會尋找檔案並檢查其日期。 如果輸出檔早於輸入檔，或如果找不到輸出檔，則會執行自訂建置工具。 如果所有**其他相依性**檔案都早於輸入檔，且輸入檔早於**輸出**屬性中指定的檔案，則不會執行自訂建置工具。

如果您想要讓建置系統操作自訂建置工具所產生的輸出檔，您必須手動將它新增至專案。 自訂建置工具會在建置期間更新檔案。

## <a name="example"></a>範例

假設您想要在專案中包含名為 parser.l 的檔案。 您的可執行檔路徑中有語彙分析器 **lexer.exe**。 您想要使用它來處理 parser.l，以產生具有相同基底名稱的 .c 檔案 (parser.c)。

首先，將 parser.l 和 parser.c 新增至專案。 如果檔案尚不存在，請新增檔案的參考。 為 parser.l 建立自訂建置工具，並在 [命令]**** 屬性中輸入下列命令：

> **lexer %(完整路徑) .\%(檔名).c**

此命令會對 parser.l 執行語彙分析器，並將 parser.c 輸出至專案目錄。

在 [輸出]**** 屬性中，輸入下列命令：

> **.\%（Filename）。c**

當您建置專案時，建置系統會比較 parser.l 和 parser.c 的時間戳記。 如果 parser.l 比較新，或如果 parser.c 不存在，則建置系統會執行 [命令列]**** 屬性的值，讓 parser.c 處於最新狀態。 由於 parser.c 也已新增至專案，因此建置系統會接著編譯 parser.c。

## <a name="see-also"></a>請參閱

[建置命令和屬性的一般巨集](reference/common-macros-for-build-commands-and-properties.md)<br>
[為組建自訂進行疑難排解](troubleshooting-build-customizations.md)
