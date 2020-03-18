---
title: 執行 LIB
description: 描述您可以搭配 lib 使用的命令列選項。
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
ms.openlocfilehash: 871b92809f38b4dcbf84de802b1ac9940ea6f1e9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438946"
---
# <a name="running-lib"></a>執行 LIB

您可以使用各種命令列選項來控制 LIB。

## <a name="lib-command-line"></a>LIB 命令列

若要執行 LIB，請輸入命令 `lib`，後面接著您要使用 LIB 之工作的選項和檔案名。 LIB 也接受命令檔中的命令列輸入，如下一節所述。 LIB 不會使用環境變數。

## <a name="lib-command-files"></a>LIB 命令檔

您可以使用下列語法，將命令列引數傳遞至命令檔中的 LIB：

> **LIB \@** <em>命令</em>檔

File*命令*檔是文字檔。 @ 符號（ **\@** ）和檔案名之間不允許有空格或定位字元。 *命令檔案名*沒有預設副檔名。 指定完整的檔案名，包括任何延伸模組。 無法使用萬用字元。 您可以使用檔案名來指定絕對或相對路徑。

在命令檔中，引數可以用空格或索引標籤分隔，如同它們可以在命令列上。 引數也可以用分行符號分隔。 使用分號（ **;** ）來標示批註。 LIB 會忽略從分號到行尾的所有文字。

您可以在命令檔中指定全部或部分的命令列，而且可以在 LIB 命令中使用一個以上的命令檔。 LIB 會接受命令檔輸入，如同在命令列上指定的位置一樣。 命令檔無法加以嵌套。 除非使用 **/nologo**選項，否則 LIB 會回顯命令檔的內容。

## <a name="using-lib-options"></a>使用 LIB 選項

選項包含選項規範，也就是破折號（ **-** ）或正斜線（ **/** ），後面接著選項的名稱。 選項名稱不可以是縮寫。 有些選項會接受引數，並在冒號（ **：** ）之後指定。 選項規格中不允許有空格或索引標籤。 在命令列上使用一或多個空格或索引標籤來分隔選項規格。 選項名稱及其關鍵字或檔案名引數不區分大小寫，但是當做引數使用的識別碼會區分大小寫。 LIB 會依照命令列和命令檔中指定的順序來處理選項。 如果使用不同的引數重複選項，則最後一個要處理的會優先。

下列選項適用于所有的 LIB 模式：

> **/ERRORREPORT** \[**無** &#124; **提示** &#124; **QUEUE**佇列&#124; **傳送**]

/ERRORREPORT 選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

> **/LINKREPRO：** _目錄-路徑_ \
> **/LINKREPROTARGET：** _filename_

若要協助 Microsoft 診斷 lib 的當機和內部錯誤，您可以使用[/LINKREPRO](linkrepro.md)選項。 此選項會產生*連結重現*，這是一組組建成品，可讓 Microsoft 重現媒體櫃操作期間發生的問題。 [/LINKREPROTARGET](linkreprotarget.md)選項可以搭配 **/LINKREPRO**選項使用。 當 lib 產生指定的檔案時，它只會產生連結重現構件。 如需詳細資訊，請參閱[如何回報 Microsoft C++工具組的問題](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

> **/LTCG**

「LTCG」代表*連結時間程式碼產生*。 這項功能需要編譯器（[cl](compiler-options.md)）、LIB 和連結器（[連結](linker-options.md)）之間的合作。 它們一起可以將程式碼優化，而不是任何元件本身所能執行的動作。

LIB 的 **/ltcg**選項指定來自 cl 的輸入包含使用[/gl](gl-whole-program-optimization.md)編譯器選項所產生的物件檔案。 如果 LIB 遇到這類輸入，而且未指定 **/ltcg** ，則會在顯示參考訊息之後，以已啟用/ltcg 的方式重新開機。 換句話說，不需要明確設定此選項，但它會加速組建效能。 這是因為 LIB 不需要自行重新開機。

在組建程式中，LIB 的輸出會傳送至連結。 連結有自己各自的 **/ltcg**選項。 它可用來執行各種優化，包括整個程式優化和特性指引優化（PGO）檢測。 如需連結選項的詳細資訊，請參閱[/ltcg](ltcg-link-time-code-generation.md)。

> **/MACHINE**

指定程式的目標平臺。 通常，您不需要指定 **/MACHINE**。 LIB 會從 .obj 檔案推斷電腦類型。 不過，在某些情況下，LIB 無法判斷電腦類型併發出錯誤訊息。 如果發生這類錯誤，請指定 **/MACHINE**。 在 **/EXTRACT**模式中，此選項僅供驗證之用。 請在命令列使用 `lib /?`，以查看可用的電腦類型。

> **/NOLOGO**

隱藏 LIB 著作權訊息和版本號碼的顯示，並防止回顯命令檔。

> **/VERBOSE**

顯示會話進度的詳細資料，包括正在新增的 .obj 檔案的名稱。 資訊會傳送至標準輸出，並且可重新導向至檔案。

> **/WX**[ **： NO**]

將警告視為錯誤。 如需詳細資訊，請參閱 [/WX (將連結器警告視為錯誤)](wx-treat-linker-warnings-as-errors.md)。

其他選項僅適用于 LIB 的特定模式。 這些選項會在描述每個模式的章節中討論。

## <a name="see-also"></a>另請參閱

[LIB 參考](lib-reference.md)
