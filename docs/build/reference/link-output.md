---
title: LINK 輸出
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 819ac130d2f8ae45ff48a2f2c1941f717d5afd99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464137"
---
# <a name="link-output"></a>LINK 輸出

Link 輸出包含.exe 檔案、 Dll、 對應檔和訊息。

##  <a name="_core_output_files"></a> 輸出檔案

連結的預設輸出檔案是.exe 檔。 如果[/DLL](../../build/reference/dll-build-a-dll.md)指定選項時，將組建連結的.dll 檔案。 您可以控制在輸出檔名[輸出檔名稱 (/out)](../../build/reference/out-output-file-name.md)選項。

在累加模式中，連結會建立.ilk 檔，以保存稍後累加建置程式的狀態資訊。 如需有關.ilk 檔的詳細資訊，請參閱[.ilk 檔](../../build/reference/dot-ilk-files-as-linker-input.md)。 如需有關累加連結的詳細資訊，請參閱 <<c0> [ 以累加方式連結 (/incremental)](../../build/reference/incremental-link-incrementally.md)選項。

當連結建立匯出 (通常是 DLL) 包含的程式，也能.lib 檔時，除非組建中使用.exp 檔。 您可以控制在匯入程式庫檔名[/IMPLIB](../../build/reference/implib-name-import-library.md)選項。

如果[產生對應檔 (/map)](../../build/reference/map-generate-mapfile.md)指定選項時，連結會建立對應檔。

如果[產生偵錯資訊 (/debug)](../../build/reference/debug-generate-debug-info.md)指定選項時，連結會建立包含程式的偵錯資訊的 PDB。

##  <a name="_core_other_output"></a> 其他輸出

當您輸入`link`而無需任何其他命令列的輸入，連結會顯示彙總其選項的使用方式陳述式。

連結會顯示著作權和版本的訊息，並回應輸入的命令檔，除非[隱藏程式啟始資訊 (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md)選項使用。

您可以使用[列印進度訊息 (/verbose)](../../build/reference/verbose-print-progress-messages.md)選項可顯示有關組建的其他詳細資料。

連結會發出錯誤和警告訊息形式 LNK*nnnn*。 此錯誤的前置詞和範圍的數字也會使用 LIB、 DUMPBIN 和 EDITBIN。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)