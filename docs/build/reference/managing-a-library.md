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
ms.openlocfilehash: 69cd03e029d014b9b74a8688f155dfb1f023b55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477060"
---
# <a name="managing-a-library"></a>管理程式庫

LIB 的預設模式是建立或修改之 COFF 物件程式庫。 當您未指定 /EXTRACT （若要將物件複製到檔案中） 或 /DEF （若要建置匯入程式庫），在此模式會執行 LIB。

若要建立從物件和/或程式庫的程式庫，使用下列語法：

```
LIB [options...] files...
```

此命令會從一或多個輸入來建立文件庫*檔案*。 *檔案*可以 COFF 物件檔案、 32 位元 OMF 目的檔或現有的 COFF 程式庫。 LIB 會建立一個程式庫，其中包含指定的檔案中的所有物件。 如果輸入的檔是 32 位元 OMF 物件檔案，程式庫將它轉換成 COFF 建置程式庫之前。 LIB 無法接受 16 位元版本的程式庫所建立的文件庫中的 32 位元 OMF 物件。 您必須先擷取物件; 使用 16 位元程式庫然後您可以使用擷取的物件檔案做為 32 位元程式庫的輸入。

根據預設，程式庫名稱使用的基底名稱的第一個物件或程式庫檔案和延伸模組的輸出檔。 lib。 輸出檔案會放在目前的目錄。 如果已經存在具有相同名稱的檔案，輸出檔案會取代現有的檔案。 若要保留現有的程式庫，請使用 /OUT 選項指定輸出檔案的名稱。

下列選項適用於建立和修改文件庫：

**/LIBPATH:** *dir*<br/>
覆寫環境程式庫路徑。 如需詳細資訊，請參閱連結描述[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項。

**/ 清單**<br/>
標準輸出中顯示輸出程式庫的相關資訊。 輸出可以重新導向至檔案。 您可以使用 /LIST 來判斷現有的程式庫的內容，而不需要修改它。

**/ 名稱：** *檔名*<br/>
當建置匯入程式庫時，指定正在建置匯入程式庫 DLL 的名稱。

**/NODEFAULTLIB**<br/>
解析外部參考時，它會搜尋程式庫清單中移除一或多個預設程式庫。 請參閱[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)如需詳細資訊。

**/ OUT:** *檔名*<br/>
覆寫預設的輸出檔案名稱。 預設情況下，輸出程式庫會建立在目前目錄中，使用命令列] 和 [延伸模組上的第一個文件庫或物件檔案的基底名稱。 lib。

**/ 移除：** *物件*<br/>
省略指定*物件*從輸出程式庫。 LIB 會合併所有的物件 （不論位於目的檔或程式庫），然後再將其刪除以 /REMOVE 指定的任何物件建立輸出程式庫。

**/SUBSYSTEM:**{**主控台** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM**&AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **原生** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [，#[。 # #]]<br/>
告知作業系統如何執行程式，建立連結至輸出程式庫。 如需詳細資訊，請參閱連結描述[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)選項。

在命令列上指定的 LIB 選項不區分大小寫。

您可以使用程式庫來執行下列的媒體櫃管理工作：

- 若要將物件加入至文件庫中，指定現有的程式庫的檔案名稱和新物件的檔案名稱。

- 若要結合程式庫，請指定程式庫檔案名稱。 您可以加入物件，並使用單一的 LIB 命令結合程式庫。

- 若要取代為新的物件程式庫成員，指定包含要被取代的成員物件的程式庫和新的物件 （或包含它的程式庫） 的檔案名稱。 當具有相同名稱的物件存在於一個以上的輸入檔中時，LIB 會變成 LIB 命令中指定輸出程式庫的最後一個物件。 當您取代程式庫成員時，請務必包含舊物件的程式庫之後，指定新的物件或程式庫。

- 若要從程式庫中刪除成員，使用 [/REMOVE] 選項。 LIB 處理 /REMOVE 合併所有的輸入的物件，不論命令列的順序之後的任何規格。

> [!NOTE]
>  您無法同時刪除的成員，並將它解壓縮到相同的步驟中的檔案。 您必須先擷取成員物件，其使用 /EXTRACT，然後再執行一次使用 /REMOVE 程式庫。 此行為與 16 位元 LIB （適用於 OMF 程式庫），在其他 Microsoft 產品中提供的不同。

## <a name="see-also"></a>另請參閱

[LIB 參考](../../build/reference/lib-reference.md)