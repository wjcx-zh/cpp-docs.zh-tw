---
title: "管理程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLibrarianTool.IgnoreAllDefaultLibraries"
  - "VC.Project.VCLibrarianTool.AdditionalDependencies"
  - "VC.Project.VCLibrarianTool.RemoveObjects"
  - "VC.Project.VCLibrarianTool.LibraryPaths"
  - "VC.Project.VCLibrarianTool.OutputFile"
  - "VC.Project.VCLibrarianTool.IgnoreDefaultLibraryNames"
  - "VC.Project.VCLibrarianTool.AdditionalLibraryDirectories"
  - "VC.Project.VCLibrarianTool.ListContentsFile"
  - "VC.Project.VCLibrarianTool.ListContents"
  - "VC.Project.VCLibrarianTool.SubSystemVersion"
  - "VC.Project.VCLibrarianTool.IgnoreDefaultLibraryName"
  - "VC.Project.VCLibrarianTool.SubSystem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CONVERT 程式庫管理員選項"
  - "/LIBPATH 程式庫管理員選項"
  - "/LINK50COMPAT 程式庫管理員選項"
  - "/LIST 程式庫管理員選項"
  - "/OUT 程式庫管理員選項"
  - "/REMOVE 程式庫管理員選項"
  - "/SUBSYSTEM 程式庫管理員選項"
  - "CONVERT 程式庫管理員選項"
  - "-CONVERT 程式庫管理員選項"
  - "LIB [C++], 管理 COFF 程式庫"
  - "LIBPATH 程式庫管理員選項"
  - "-LIBPATH 程式庫管理員選項"
  - "LINK50COMPAT 程式庫管理員選項"
  - "-LINK50COMPAT 程式庫管理員選項"
  - "LIST 程式庫管理員選項"
  - "-LIST 程式庫管理員選項"
  - "目的檔"
  - "目的檔, 建置和修改"
  - "OUT 程式庫管理員選項"
  - "-OUT 程式庫管理員選項"
  - "REMOVE 程式庫管理員選項"
  - "-REMOVE 程式庫管理員選項"
  - "SUBSYSTEM 程式庫管理員選項"
  - "-SUBSYSTEM 程式庫管理員選項"
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 管理程式庫
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

預設的 LIB 模式是建立或修改 COFF 物件程式庫。  當您沒有指定 \/EXTRACT \(將物件複製到檔案\) 或 \/DEF \(建置匯入程式庫\) 時，LIB 會以這種模式執行。  
  
 若要從物件和 \(或\) 程式庫建置程式庫，請使用下列語法：  
  
```  
LIB [options...] files...  
```  
  
 這個命令會從一或多個輸入檔 \(*files*\) 建立程式庫。  *files* 可以是 COFF 目的檔、32 位元 OMF 目的檔或現有的 COFF 程式庫。  LIB 會建立包含指定檔案中所有物件的程式庫。  如果輸入檔案是 32 位元 OMF 目的檔，LIB 在建置程式庫前將其轉換為 COFF。  LIB 不能接受由 16 位元版本的 LIB 所建立之程式庫中的 32 位元 OMF 物件。  您必須先使用 16 位元的 LIB 來引出物件，然後您可以使用引出的目的檔作做為 32 位元 LIB 的輸入。  
  
 根據預設，LIB 使用第一個目的檔或程式庫檔案的主檔名 \(Base Name\) 和副檔名 .lib 來命名輸出檔案。  輸出檔案會放置在目前的目錄中。  如果有相同名稱的檔案已經存在，輸出檔會取代現有的檔案。  若要保留現有的程式庫，請使用 \/OUT 選項來指定輸出檔案的名稱。  
  
 下列選項可套用在建置和修改程式庫：  
  
 \/LIBPATH: `dir`  
 覆寫環境程式庫路徑。  如需詳細資訊，請參閱 LINK [\/LIBPATH](../../build/reference/libpath-additional-libpath.md) 選項的描述。  
  
 \/LIST  
 將有關輸出程式庫的資訊顯示於標準輸出。  輸出可以重新導向至檔案中。  您可以使用 \/LIST 來判斷現有程式庫的內容而不改變它。  
  
 \/NAME: *filename*  
 當建置匯入程式庫時，指定正在建置之匯入程式庫的 DLL 名稱。  
  
 \/NODEFAULTLIB  
 從解析外部參考時所搜尋的程式庫清單，移除一個或多個預設程式庫。  如需詳細資訊，請參閱 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)。  
  
 \/OUT: *filename*  
 覆寫預設輸出檔案名稱。  根據預設，輸出程式庫會建立在目前的目錄中，並具有命令列之第一個程式庫或目的檔的主檔名和副檔名 .lib。  
  
 \/REMOVE: *object*  
 從輸出程式庫省略指定的物件 \(*object*\)。  LIB 會合併所有的物件 \(不論位於目的檔或程式庫\) 來建立輸出程式庫，然後刪除以 \/REMOVE 指定的任何物件。  
  
 \/SUBSYSTEM:{CONSOLE &#124; EFI\_APPLICATION &#124; EFI\_BOOT\_SERVICE\_DRIVER &#124; EFI\_ROM &#124; EFI\_RUNTIME\_DRIVER &#124; NATIVE &#124; POSIX &#124; WINDOWS &#124; WINDOWSCE}\[,\#\[.\#\#\]\]  
 告訴作業系統如何執行藉由連結到輸出程式庫而建立的程式。  如需詳細資訊，請參閱 LINK [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 選項中的描述。  
  
 在命令列指定的 LIB 選項不區分大小寫。  
  
 您可以使用 LIB 來執行下列的程式庫管理工作：  
  
-   若要將物件加入至程式庫，請指定現有程式庫檔名和新物件的檔名。  
  
-   若要合併程式庫，請指定程式庫檔名。  您可以用一個 LIB 命令來加入物件並合併程式庫。  
  
-   若要以新的物件取代某程式庫成員，請指定包含要取代之成員物件的程式庫，和新物件 \(或是包含它的程式庫\) 的檔名。  當相同名稱的物件存在於一個以上的輸入檔案中，LIB 會將在 LIB 命令中指定的最後一個物件放入輸出程式庫。  當您取代程式庫成員時，請將新的物件或程式庫指定於包含舊物件之程式庫的後面。  
  
-   若要從程式庫刪除一個成員，請使用 \/REMOVE 選項。  LIB 會在合併所有輸入物件後處理 \/REMOVE 的任何規格，不管命令列的順序。  
  
> [!NOTE]
>  您不能在同一個步驟中，同時刪除一個成員，又將其引出到檔案中。  您必須使用 \/EXTRACT 先引出成員物件，然後使用 \/REMOVE 再執行 LIB 一次。  這個動作與在其他 Microsoft 產品所提供之 16 位元的 LIB \(適用 OMF 程式庫\) 不同。  
  
## 請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)