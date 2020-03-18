---
title: LIB 概觀
description: 程式庫工具（lib）的使用方式和選項。
ms.date: 02/09/2020
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 4ed725f383d956adf7abcf1c68002dee51703013
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439009"
---
# <a name="overview-of-lib"></a>LIB 概觀

在建立程式時，LIB （lib）會建立標準程式庫、匯入[連結](linker-options.md)庫和匯出檔案。 LIB 會從命令提示字元執行。

您可以在下列模式中使用 LIB：

- [建立或修改 COFF 程式庫](managing-a-library.md)

- [將成員物件解壓縮至檔案](extracting-a-library-member.md)

- [建立匯出檔案和匯入程式庫](working-with-import-libraries-and-export-files.md)

這些模式是互斥的;您一次只能在一個模式中使用 LIB。

## <a name="lib-options"></a>LIB 選項

下表列出 lib 的選項，並提供詳細資訊的連結。

|選項|描述|
|-|-|
|**/DEF**|建立匯入程式庫和匯出檔案。<br/><br/>如需詳細資訊，請參閱[建立匯入程式庫和匯出](building-an-import-library-and-export-file.md)檔案。|
|**/ERRORREPORT**| 已被取代。 如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/EXPORT**|   從您的程式匯出函式。<br/><br/>如需詳細資訊，請參閱[建立匯入程式庫和匯出](building-an-import-library-and-export-file.md)檔案。|
|**/EXTRACT**|   建立包含現有文件庫成員複本的物件（.obj）檔案。<br/><br/>如需詳細資訊，請參閱[解壓縮程式庫成員](extracting-a-library-member.md)。|
|**/INCLUDE**|   將符號加入至符號表。<br/><br/>如需詳細資訊，請參閱[建立匯入程式庫和匯出](building-an-import-library-and-export-file.md)檔案。|
|**/LIBPATH**|   覆寫環境程式庫路徑。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/LINKREPRO**|   建立重現 lib 損毀或內部錯誤所需的成品。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/LINKREPROTARGET**|   只有在搭配指定的檔案使用 lib 時，才會產生 **/LINKREPRO**構件。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/LIST**|   將輸出程式庫的相關資訊顯示為標準輸出。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/LTCG**|   使用連結時產生程式碼，來建立程式庫。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/MACHINE**|   指定程式的目標平臺。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/NAME**|   建立匯入程式庫時，指定要為其建立匯入程式庫的 DLL 名稱。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/NODEFAULTLIB**|   從解析外部參考時所搜尋的程式庫清單中移除一或多個預設程式庫。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/NOLOGO**|   隱藏 LIB 著作權訊息和版本號碼的顯示，並防止回顯命令檔。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/OUT**|   覆寫預設輸出檔案名。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/REMOVE**|   省略輸出程式庫中的物件。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/SUBSYSTEM**|   告訴作業系統如何執行藉由連結至輸出庫而建立的程式。<br/><br/>如需詳細資訊，請參閱[管理程式庫](managing-a-library.md)。|
|**/VERBOSE**|   顯示會話進度的詳細資料，包括正在新增的 .obj 檔案的名稱。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|
|**/WX**|   將警告視為錯誤。<br/><br/>如需詳細資訊，請參閱[執行 LIB](running-lib.md)。|

## <a name="see-also"></a>另請參閱

[LIB 參考](lib-reference.md)\
[LIB 輸入](lib-input-files.md)檔\
[LIB 輸出](lib-output-files.md)檔案\
[其他 LIB 輸出](other-lib-output.md)\
[程式庫結構](structure-of-a-library.md)
