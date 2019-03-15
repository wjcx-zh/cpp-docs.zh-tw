---
title: EDITBIN 選項
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: e7338c6a45d74aa8efac1b72683cca7661c62e0a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820100"
---
# <a name="editbin-options"></a>EDITBIN 選項

您可以使用 EDITBIN 來修改物件的檔案、 可執行檔，以及動態連結程式庫 (Dll)。 選項會指定 EDITBIN 所做的變更。

選項選項規範組成，這是一個破折號 （-） 或斜線 （/），後面加上選項的名稱。 選項名稱不能被縮寫。 某些選項可接受於冒號 ( : ) 之後指定的引數。 內的選項規格允許沒有空格或定位字元。 使用一個或多個空間索引標籤來分隔命令列上的選項規格。 選項名稱及其關鍵字引數或檔名引數不區分大小寫。 例如，-bind 和 /BIND 意義相同。

EDITBIN 具有下列選項：

|選項|用途|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|指定 DLL 是否可以繫結。|
|[/ALLOWISOLATION](allowisolation.md)|指定 DLL 或可執行檔資訊清單查閱行為。|
|[/APPCONTAINER](appcontainer.md)|指定是否必須在 AppContainer 中執行應用程式 — 例如，UWP 應用程式。|
|[/BIND](bind.md)|在指定的物件中設定進入點位址，以加速載入時間。|
|[/DYNAMICBASE](dynamicbase.md)|指定 DLL 或可執行檔映像是否可以使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重定基底。|
|[/ERRORREPORT](errorreport-editbin-exe.md)|向 Microsoft 報告內部錯誤。|
|[/HEAP](heap.md)|設定可執行檔映像的堆積大小 (位元組)。|
|[/HIGHENTROPYVA](highentropyva.md)|指定 DLL 或可執行映像是否支援高熵 (64 位元) 位址空間配置隨機載入 (ASLR)。|
|[/INTEGRITYCHECK](integritycheck.md)|指定是否在載入時間檢查數位簽章。|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|指定物件是否支援大於 2 GB 的位址。|
|[/NOLOGO](nologo-editbin.md)|隱藏 EDITBIN 程式啟始資訊。|
|[/NXCOMPAT](nxcompat.md)|指定可執行映像是否與 Windows 資料執行防止功能相容。|
|[/REBASE](rebase.md)|設定指定之物件的基底位址。|
|[/RELEASE](release.md)|在標頭中設定總和檢查碼。|
|[/SECTION](section-editbin.md)|覆寫區段的屬性。|
|[/STACK](stack.md)|設定可執行檔映像的堆疊大小 (位元組)。|
|[/SUBSYSTEM](subsystem.md)|指定執行環境。|
|[/SWAPRUN](swaprun.md)|指定可執行檔映像必須複製到分頁檔，再從分頁檔執行映像。|
|[/TSAWARE](tsaware.md)|指定應用程式是設計成在多使用者環境中執行。|
|[/VERSION](version.md)|在標頭中設定版本號碼。|

## <a name="see-also"></a>另請參閱

[其他 MSVC 建置工具](c-cpp-build-tools.md)<br/>
[EDITBIN 參考](editbin-reference.md)
