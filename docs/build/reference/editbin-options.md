---
title: EDITBIN 選項
description: Microsoft EDITBIN 公用程式命令列選項的參考指南。
ms.date: 02/09/2020
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: 9fd4170e5ee020780963d83936f1a9fd08d2be11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439968"
---
# <a name="editbin-options"></a>EDITBIN 選項

您可以使用 EDITBIN 來修改物件檔案、可執行檔和動態連結程式庫（Dll）。 選項會指定 EDITBIN 所做的變更。

選項包含選項規範，也就是破折號（`-`）或正斜線（`/`），後面接著選項的名稱。 選項名稱不可以是縮寫。 有些選項會採用冒號（`:`）後面指定的引數。 選項規格中不允許有空格或索引標籤。 在命令列上使用一或多個空格或索引標籤來分隔選項規格。 選項名稱及其關鍵字引數或檔案名引數不區分大小寫。 例如，`-bind` 和 `/BIND` 表示相同的東西。

EDITBIN 有下列選項：

|選項|目的|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|指定 DLL 是否可以繫結。|
|[/ALLOWISOLATION](allowisolation.md)|指定 DLL 或可執行檔資訊清單查閱行為。|
|[/APPCONTAINER](appcontainer.md)|指定應用程式是否必須在 AppContainer 中執行（例如 UWP 應用程式）。|
|[/BIND](bind.md)|在指定的物件中設定進入點位址，以加速載入時間。|
|[/DYNAMICBASE](dynamicbase.md)|指定 DLL 或可執行檔映像是否可以使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重定基底。|
|[/ERRORREPORT](errorreport-editbin-exe.md)| 已被取代。 錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。 |
|[/HEAP](heap.md)|設定可執行映射的堆積大小（以位元組為單位）。|
|[/HIGHENTROPYVA](highentropyva.md)|指定 DLL 或可執行映像是否支援高熵 (64 位元) 位址空間配置隨機載入 (ASLR)。|
|[/INTEGRITYCHECK](integritycheck.md)|指定是否在載入時間檢查數位簽章。|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|指定物件是否支援大於 2 GB 的位址。|
|[/NOLOGO](nologo-editbin.md)|隱藏 EDITBIN 程式啟始資訊。|
|[/NXCOMPAT](nxcompat.md)|指定可執行映像是否與 Windows 資料執行防止功能相容。|
|[/REBASE](rebase.md)|設定指定之物件的基底位址。|
|[/RELEASE](release.md)|在標頭中設定總和檢查碼。|
|[/SECTION](section-editbin.md)|覆寫區段的屬性。|
|[/STACK](stack.md)|設定可執行檔映射的堆疊大小（以位元組為單位）。|
|[/SUBSYSTEM](subsystem.md)|指定執行環境。|
|[/SWAPRUN](swaprun.md)|指定可執行映射複製到分頁檔，然後從該處執行。|
|[/TSAWARE](tsaware.md)|指定應用程式是設計成在多使用者環境中執行。|
|[/VERSION](version.md)|在標頭中設定版本號碼。|

## <a name="see-also"></a>另請參閱

[其他 MSVC build 工具](c-cpp-build-tools.md)\
[EDITBIN 參考](editbin-reference.md)
