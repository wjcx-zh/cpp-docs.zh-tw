---
title: 管理程式庫
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336399"
---
# <a name="managing-a-library"></a>管理程式庫

LIB 的預設模式是生成或修改 COFF 物件庫。 如果不指定 /EXTRACT(將物件複製到檔案)或 /DEF(生成導入庫),LIB 將在此模式下運行。

要從物件和/或庫產生庫,請使用以下語法:

```
LIB [options...] files...
```

此命令從一個或多個輸入*檔案*建立庫。 *這些檔*可以是 COFF 物件檔、32 位元 OMF 物件檔或現有的 COFF 庫。 LIB 創建一個庫,其中包含指定檔中的所有物件。 如果輸入檔是 32 位 OMF 物件檔,LIB 在建譯庫之前將其轉換為 COFF。 LIB 不能接受由 16 位元版本的 LIB 創建的庫中的 32 位 OMF 物件。 您必須首先使用 16 位 LIB 提取物件;因此,您必須首先使用 16 位 LIB 來提取物件。然後,您可以使用提取的物件文件作為 32 位 LIB 的輸入。

預設情況下,LIB 使用第一個物件或庫檔的基本名稱以及擴展名 .lib 命名輸出檔。 輸出檔放在當前目錄中。 如果檔已存在同名檔,則輸出檔將替換現有檔。 要保留現有函式庫,請使用 /OUT 選項為輸出檔指定名稱。

以下選項適用於建構與修改函式庫:

**/LIBPATH:** *dir*<br/>
覆寫環境程式庫路徑。 有關詳細資訊,請參閱[LINK/LIBPATH](libpath-additional-libpath.md)選項的說明。

**/LIST**<br/>
顯示有關輸出庫到標準輸出的資訊。 輸出可以重定向到檔。 您可以使用 /LIST 來確定現有庫的內容,而無需對其進行修改。

**/NAME:***檔案名稱*<br/>
生成導入庫時,指定正在為其產生導入庫的 DLL 的名稱。

**/NODEFAULTLIB**<br/>
從解析外部引用時搜索的庫清單中刪除一個或多個預設庫。 有關詳細資訊,請參閱[/NODEFAULTLIB。](nodefaultlib-ignore-libraries.md)

**/OUT:***檔案名稱*<br/>
覆蓋預設輸出檔名。 預設情況下,輸出庫在當前目錄中創建,命令列上的第一個庫或物件檔的基本名稱以及擴展點 .lib。

**/REMOVE:***物件*<br/>
從輸出庫中省略指定的*物件*。 LIB 通過合併所有物件(無論是在物件文件還是庫中),然後刪除使用 /REMOVE 指定的任何對象來創建輸出庫。

**/SUBSYSTEM:** **WINDOWS** [ **&#124;EFI_APPLICATION&#124;&#124;EFI_BOOT_SERVICE_DRIVER** **CONSOLE** **&#124;EFI_ROMEFI_ROM** **EFI_ROM** **POSIX** **&#124;EFI_RUNTIME_DRIVER&#124;****本機**&#124; &#124; **WINDOWS&#124;** WINDOWS_______________&#124; &#124;&#124;&#124;&#124;<br/>
告訴作業系統如何運行透過連結到輸出庫創建的程式。 有關詳細資訊,請參閱[LINK/SUBSYSTEM](subsystem-specify-subsystem.md)選項的說明。

在命令列上指定的 LIB 選項不區分大小寫。

您可以使用 LIB 執行以下函式庫管理工作:

- 要將物件添加到庫,請指定現有庫的檔名和新物件的檔名。

- 要合併庫,請指定庫檔名。 您可以添加物件並將庫與單個 LIB 命令合併。

- 要將庫成員替換為新物件,請指定包含要替換的成員物件的庫以及新物件(或包含該物件的庫)的檔名。 當多個輸入檔中存在具有相同名稱的物件時,LIB 會將 LIB 命令中指定的最後一個物件放入輸出庫中。 替換庫成員時,請確保在包含舊物件的庫之後指定新物件或庫。

- 要從庫中刪除成員,請使用 /REMOVE 選項。 LIB 在組合所有輸入物件后處理 /REMOVE 的任何規範,而不考慮命令行順序。

> [!NOTE]
> 不能同時刪除成員並將其提取到同一步驟中的檔。 您必須首先使用 /EXTRACT 提取成員物件,然後使用 /REMOVE 再次運行 LIB。 此行為不同於其他 Microsoft 產品中提供的 16 位 LIB(用於 OMF 庫)。

## <a name="see-also"></a>另請參閱

[LIB 參考](lib-reference.md)
