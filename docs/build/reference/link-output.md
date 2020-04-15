---
title: LINK 輸出
ms.date: 11/04/2016
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331784"
---
# <a name="link-output"></a>LINK 輸出

連結輸出包括 .exe 檔、DLL、地圖檔和消息。

## <a name="output-files"></a><a name="_core_output_files"></a>輸出檔案

LINK 的預設輸出檔是 .exe 檔案。 如果指定[了 /DLL](dll-build-a-dll.md)選項,LINK 將生成 .dll 檔。 您可以使用[輸出檔名 (/OUT)](out-output-file-name.md)選項控制輸出檔名。

在增量模式下,LINK 創建一個 .ilk 檔案,用於保存程式以後增量生成的狀態資訊。 有關 .ilk 檔案的詳細資訊,請參閱[.ilk 檔案](dot-ilk-files-as-linker-input.md)。 有關增量連結的詳細資訊,請參閱[連結增量連結(/增量)](incremental-link-incrementally.md)選項。

當 LINK 創建包含匯出的程式(通常是 DLL)時,它還會生成 .lib 檔,除非生成中使用了 .exp 檔。 您可以使用[/IMPLIB](implib-name-import-library.md)選項控制匯入庫檔名。

如果指定了[「生成地圖檔(/MAP)」](map-generate-mapfile.md)選項,LINK 將創建一個地圖檔。

如果指定了[生成除錯資訊 (/DEBUG)](debug-generate-debug-info.md)選項,LINK 將創建一個 PDB 以包含該程式的調試資訊。

## <a name="other-output"></a><a name="_core_other_output"></a>其他輸出

當您在沒有任何`link`任何其他命令列輸入的情況下鍵入時,LINK 將顯示一個用法語句,該語句彙總其選項。

LINK 顯示版權和版本消息並回顯命令檔輸入,除非使用[「抑制啟動橫幅 (/NOLOGO)」](nologo-suppress-startup-banner-linker.md)選項。

您可以使用[「列印進度訊息(/VERBOSE)」](verbose-print-progress-messages.md)選項來顯示有關生成的其他詳細資訊。

LINK 在 LNK*nnnn*窗體中發出錯誤和警告消息。 LIB、DUMPBIN 和 EDITBIN 也使用此錯誤前綴和數位範圍。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
