---
title: 執行 LIB |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff75c149ff3cfff5a360314386cc4828d00f4e8d
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894599"
---
# <a name="running-lib"></a>執行 LIB

命令列的各種選項可用來控制 LIB。

## <a name="lib-command-line"></a>LIB 命令列

若要執行 LIB，輸入命令`lib`後面的選項和工作的檔案名稱您使用程式庫來執行。 LIB 也接受命令列輸入命令檔下, 一節所述。 程式庫不會使用環境變數。

> [!NOTE]
> 如果您習慣 LINK32.exe 及 LIB32.exe 工具，提供與 Microsoft Win32 軟體開發套件的 Windows NT 中，您可能已使用其中一個命令`link32 -lib`或命令`lib32`用於管理程式庫及建立匯入程式庫。 請務必變更 makefile 和批次檔，以使用`lib`命令。

## <a name="lib-command-files"></a>LIB 命令檔

您可以將命令列引數傳遞到命令檔，請使用下列語法中的 LIB:

> **LIB \@**  <em>commandfile&lt</em>

檔案*commandfile&lt*是文字檔案。 允許之間沒有空格或定位字元 at 符號 (**\@**) 和檔案名稱。 沒有任何預設的延伸模組;您必須指定完整的檔名，包括任何副檔名。 無法使用萬用字元。 您可以指定絕對或相對路徑與檔案名稱。

在命令檔中，引數可以如同他們可以在命令列; 上的空格或定位點，以分隔它們也可以以新行字元分隔。 您可以使用分號 （;） 來標記註解。 LIB 會忽略從分號到行結尾的所有文字。

您可以在命令檔中，指定所有或部分命令列，而且您可以使用 LIB 命令中的多個命令檔。 LIB 接受命令檔案輸入，如同它已指定命令列上該位置中。 不可為巢狀命令檔。 LIB 會回應命令檔案的內容，除非使用 /NOLOGO 選項。

## <a name="using-lib-options"></a>使用 LIB 選項

選項選項規範組成，這是一個破折號 （-） 或斜線 （/），後面加上選項的名稱。 選項名稱不能被縮寫。 有些選項需要引數，指定在冒號 （:） 之後。 內的選項規格允許沒有空格或定位字元。 使用一個或多個空間索引標籤來分隔命令列上的選項規格。 選項名稱和其關鍵字或檔名引數不區分大小寫，但做為引數的識別碼會區分大小寫。 LIB 處理命令列上指定的順序和命令檔中的選項。 如果選項會重複使用不同的引數，則最後一個来處理的優先順序較高。

下列選項適用於所有模式的程式庫：

> **/ERRORREPORT** [**NONE** &AMP;#124; **提示** &AMP;#124; **佇列** &AMP;#124; **傳送**]

如果 lib.exe 在執行階段失敗，您可以使用 /ERRORREPORT 有關這些內部錯誤，傳送給 Microsoft 的資訊。

如需 /ERRORREPORT 的詳細資訊，請參閱[/errorReport （回報編譯器內部錯誤）](../../build/reference/errorreport-report-internal-compiler-errors.md)。

> **/LTCG**

會導致要建置使用連結時產生程式碼程式庫。  如需詳細資訊，請參閱 < [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。

> **/ 電腦**

指定程式的目標平台。 通常，您不需要指定 /MACHINE。 LIB 會推斷.obj 檔中的機器類型。 不過，在某些情況下，LIB 無法判斷電腦類型，而且會發出錯誤訊息。 如果發生這類錯誤，請指定 /MACHINE。 在 /EXTRACT 模式中，此選項是用於驗證。 使用`lib /?`在命令列以查看可用的機器類型。

> **/NOLOGO**

隱藏顯示的 LIB 著作權訊息和版本號碼，並避免回應的命令檔。

> **/VERBOSE**

顯示進度的工作階段，包括所加入之.obj 檔的名稱相關的詳細資料。 資訊會傳送至標準輸出，並且可重新導向至檔案。

> **/WX**[**: NO**]

將警告視為錯誤。 請參閱[/WX （連結器警告視為錯誤）](../../build/reference/wx-treat-linker-warnings-as-errors.md)如需詳細資訊。

其他選項只適用於 LIB 的特定模式。 描述每一種模式的章節中討論這些選項。

## <a name="see-also"></a>另請參閱

[LIB 參考](../../build/reference/lib-reference.md)