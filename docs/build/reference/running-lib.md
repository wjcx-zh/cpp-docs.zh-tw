---
title: "執行 LIB |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
dev_langs: C++
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
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a487bb6f6ffd740f6479916c5115bf95d568655
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="running-lib"></a>執行 LIB
多種命令列選項可用來控制 LIB。  
  
## <a name="lib-command-line"></a>LIB 命令列  
 若要執行 LIB，輸入命令`lib`後面接著選項和工作的檔案名稱您正使用 LIB 來執行。 LIB 也接受下一節所述的命令檔案中的命令列輸入。 LIB 不會使用環境變數。  
  
> [!NOTE]
>  如果您習慣 LINK32.exe 及 LIB32.exe 工具，提供與 Microsoft Win32 軟體開發套件的 Windows NT，您可能已在使用任一命令`link32 -lib`或命令`lib32`管理程式庫，以及建立匯入程式庫。 請務必變更 makefile 和批次檔，以使用`lib`命令。  
  
## <a name="lib-command-files"></a>LIB 命令檔  
 您可以將命令列引數傳遞至 LIB 命令檔案中使用下列語法：  
  
```  
LIB @commandfile  
```  
  
 檔案`commandfile`是文字檔案。 沒有空格或定位點之間允許 at 符號 (@) 和檔案名稱。 沒有任何預設擴充功能。您必須指定完整的檔名，包括任何副檔名。 無法使用萬用字元。 您可以指定為絕對或相對路徑與檔案名稱。  
  
 在命令檔中，引數可分隔空格或定位點，因為它們可以在命令列;它們也可以使用新行字元分隔。 您可以使用分號 （;） 來標記註解。 LIB 會忽略從分號到行尾的所有文字。  
  
 您可以在命令檔中，指定全部或部分命令列，您可以使用一個以上的命令檔案在 LIB 命令。 LIB 接受命令檔輸入，如同它已指定命令列上的位置。 不可為巢狀命令檔。 LIB 回應命令檔案的內容，除非使用了 /NOLOGO 選項。  
  
## <a name="using-lib-options"></a>使用 LIB 選項  
 選項包含選項規範，這是虛線 （-） 或斜線 （/），後面接著選項的名稱。 選項名稱不能為縮寫。 某些選項可接受於冒號 （:） 之後指定為引數。 選項規格內允許任何空格或定位字元。 使用一個或多個空格或定位字元分隔命令列上的選項規格。 選項名稱及其關鍵字或檔名引數並不區分大小寫，但做為引數的識別碼會區分大小寫。 LIB 處理命令列上指定的順序和命令檔中的選項。 選項會重複使用不同的引數，如果要處理的最後一個的優先順序較高。  
  
 下列選項適用於所有的 LIB 模式：  
  
 /ERRORREPORT [無 &#124;提示字元 &#124;佇列 &#124;傳送]  
 如果 lib.exe 在執行階段失敗，您可以使用 /ERRORREPORT 需這些內部錯誤，將資訊傳送給 Microsoft。  
  
 如需 /ERRORREPORT 的詳細資訊，請參閱[/errorReport （回報編譯器內部錯誤）](../../build/reference/errorreport-report-internal-compiler-errors.md)。  
  
 /LTCG  
 會使用連結時產生程式碼建置程式庫。  如需詳細資訊，請參閱[/LTCG](../../build/reference/ltcg-link-time-code-generation.md)。  
  
 /MACHINE  
 指定程式的目標平台。 通常，您不需要指定 /MACHINE。 LIB 會推斷從.obj 檔案的電腦類型。 不過，在某些情況下，LIB 無法判斷電腦類型，並發出錯誤訊息。 如果發生這類錯誤，請指定 /MACHINE。 在 /EXTRACT 模式中，此選項適用於僅驗證。 使用`lib /?`在命令列以查看可用的電腦類型。  
  
 /NOLOGO  
 隱藏的 LIB 著作權訊息和版本號碼，並防止命令檔的回應。  
  
 /VERBOSE  
 顯示進度的工作階段，包括所加入之.obj 檔的名稱相關的詳細資料。 資訊會傳送至標準輸出，並且可重新導向至檔案。  
  
 /WX [: NO]  
 將警告視為錯誤。 請參閱[/WX （連結器警告視為錯誤）](../../build/reference/wx-treat-linker-warnings-as-errors.md)如需詳細資訊。  
  
 其他選項只適用於特定模式的 LIB。 各節描述每個模式中會討論這些選項。  
  
## <a name="see-also"></a>請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)