---
title: LIB 概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8fd3d370da4f841e85086e3d061508d68414e96
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379194"
---
# <a name="overview-of-lib"></a>LIB 概觀
LIB 建立標準程式庫、 匯入程式庫，和匯出的檔案，您可以使用[連結](../../build/reference/linker-options.md)時建置程式。 從命令提示字元執行 LIB。  
  
 您可以使用程式庫中的下列模式：  
  
-   [建立或修改 COFF 程式庫](../../build/reference/managing-a-library.md)  
  
-   [擷取至檔案的成員物件](../../build/reference/extracting-a-library-member.md)  
  
-   [建立匯出檔案和匯入程式庫](../../build/reference/working-with-import-libraries-and-export-files.md)  
  
 這些模式是互斥。您可以使用 LIB 中只有一個模式，一次。  
  
## <a name="lib-options"></a>Lib 選項  
 下表列出的選項 lib.exe，含有更多資訊的連結。  
  
 **/DEF**  
 建立匯入程式庫和匯出檔案。  
  
 如需詳細資訊，請參閱[建置匯入程式庫和匯出檔案](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **/ERRORREPORT**  
 內部錯誤的 lib.exe 將資訊傳送給 Microsoft。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **/EXPORT**  
 匯出函式，從您的程式。  
  
 如需詳細資訊，請參閱[建置匯入程式庫和匯出檔案](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **/ 擷取**  
 建立包含現有的程式庫之成員的複製目的檔 (.obj)。  
  
 如需詳細資訊，請參閱[引出程式庫成員](../../build/reference/extracting-a-library-member.md)。  
  
 **/INCLUDE**  
 加入至符號表的符號。  
  
 如需詳細資訊，請參閱[建置匯入程式庫和匯出檔案](../../build/reference/building-an-import-library-and-export-file.md)。  
  
 **/LIBPATH**  
 覆寫環境程式庫路徑。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/ 清單**  
 標準輸出中顯示輸出程式庫的相關資訊。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/LTCG**  
 會使用連結時產生程式碼建置程式庫。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **/ 電腦**  
 指定程式的目標平台。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **/ 名稱**  
 當建置匯入程式庫時，指定正在建置匯入程式庫 DLL 的名稱。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/NODEFAULTLIB**  
 解析外部參考時所搜尋的程式庫的清單中移除一或多個預設程式庫。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/NOLOGO**  
 隱藏的 LIB 著作權訊息和版本號碼，並防止命令檔的回應。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **/ 輸入輸出**  
 覆寫預設輸出檔名。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/ 移除**  
 省略輸出程式庫中的物件。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/SUBSYSTEM**  
 告知作業系統如何執行程式，建立連結至輸出程式庫。  
  
 如需詳細資訊，請參閱[管理程式庫](../../build/reference/managing-a-library.md)。  
  
 **/VERBOSE**  
 顯示進度的工作階段，包括所加入之.obj 檔的名稱相關的詳細資料。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
 **/WX**  
 將警告視為錯誤。  
  
 如需詳細資訊，請參閱[執行 LIB](../../build/reference/running-lib.md)。  
  
## <a name="see-also"></a>另請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)   
 [LIB 輸入的檔](../../build/reference/lib-input-files.md)   
 [LIB 輸出檔案](../../build/reference/lib-output-files.md)   
 [其他 LIB 輸出](../../build/reference/other-lib-output.md)   
 [程式庫結構](../../build/reference/structure-of-a-library.md)