---
title: 管理程式庫 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05ced49a960aea0b32365b80fe76095893f63d5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="managing-a-library"></a>管理程式庫
LIB 的預設模式是建立或修改的 COFF 物件程式庫。 當您未指定 /EXTRACT （若要將物件複製到檔案） 或 /DEF （若要建置之匯入程式庫），在此模式會執行 LIB。  
  
 若要建置程式庫物件，及/或程式庫，請使用下列語法：  
  
```  
LIB [options...] files...  
```  
  
 此命令會從一或多個輸入來建立文件庫*檔案*。 *檔案*可以 COFF 物件檔、 32 位元 OMF 目的檔或現有的 COFF 程式庫。 LIB 會建立包含指定的檔案中的所有物件的一個文件庫。 如果輸入的檔是 32 位元 OMF 目的檔，程式庫將它轉換成 COFF 之前建置程式庫。 LIB 無法接受的 32 位元 OMF 物件是 16 位元版本的 LIB 所建立的文件庫中。 您必須先使用 16 位元程式庫來擷取物件。然後您可以使用擷取的物件檔案做為 32 位元 LIB 輸入。  
  
 根據預設，程式庫名稱使用基底名稱的第一個物件或程式庫檔案和延伸模組的輸出檔。 lib。 輸出檔放在目前的目錄中。 如果檔案已經存在具有相同名稱，輸出檔會取代現有的檔案。 若要保留現有的程式庫，請使用 /OUT 選項指定輸出檔案的名稱。  
  
 下列選項適用於建置和修改文件庫：  
  
 /LIBPATH:`dir`  
 覆寫環境程式庫路徑。 如需詳細資訊，請參閱連結描述[/LIBPATH](../../build/reference/libpath-additional-libpath.md)選項。  
  
 / 清單  
 標準輸出中顯示輸出程式庫的相關資訊。 輸出可以重新導向至檔案。 您可以使用 /LIST 來判斷現有的程式庫的內容，但無法加以修改。  
  
 / NAME:*檔名*  
 當建置匯入程式庫時，指定正在建置匯入程式庫 DLL 的名稱。  
  
 /NODEFAULTLIB  
 解析外部參考時所搜尋的程式庫的清單中移除一或多個預設程式庫。 請參閱[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)如需詳細資訊。  
  
 / 輸入輸出：*檔名*  
 覆寫預設輸出檔名。 根據預設，輸出程式庫會建立在目前目錄中，第一個文件庫或物件上檔案的命令列] 和 [擴充功能的基本名稱。 lib。  
  
 / 移除：*物件*  
 省略指定*物件*從輸出程式庫。 LIB 會合併所有的物件 （不論位於目的檔或程式庫），並刪除以 /REMOVE 指定的任何物件的建立輸出程式庫。  
  
 /SUBSYSTEM: {主控台 &#124;EFI_APPLICATION &#124;時，EFI_BOOT_SERVICE_DRIVER &#124;EFI_ROM &#124;EFI_RUNTIME_DRIVER 才 &#124;原生 &#124;POSIX &#124;WINDOWS &#124;WINDOWSCE} [，#[。 # #]]  
 告知作業系統如何執行程式，建立連結至輸出程式庫。 如需詳細資訊，請參閱連結描述[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)選項。  
  
 在命令列上指定的 LIB 選項不區分大小寫。  
  
 您可以使用程式庫來執行下列的媒體櫃管理工作：  
  
-   若要將物件加入至文件庫中，指定現有的程式庫的檔案名稱和新物件的檔名。  
  
-   若要將程式庫，指定程式庫檔案名稱。 您可以加入物件，並結合單一 LIB 命令的程式庫。  
  
-   若要取代為新的物件程式庫成員，指定包含要被取代的成員物件的程式庫和新的物件 （或包含它的程式庫） 的檔案名稱。 具有相同名稱的物件存在一個以上的輸入檔中，當 LIB 就會變成輸出程式庫 LIB 命令中指定的最後一個物件。 當您取代程式庫成員時，請務必包含舊物件的程式庫之後指定新的物件或程式庫。  
  
-   若要刪除文件庫中的成員，請使用 /REMOVE 選項。 LIB 處理 /REMOVE 合併所有的輸入的物件，不論命令列的順序之後的任何規格。  
  
> [!NOTE]
>  您無法同時刪除成員，並將它解壓縮至相同的步驟中的檔案。 您必須先擷取成員物件使用 /EXTRACT，然後執行一次使用 /REMOVE LIB。 此行為不同的 16 位元 LIB （適用於 OMF 程式庫），提供其他 Microsoft 產品。  
  
## <a name="see-also"></a>請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)