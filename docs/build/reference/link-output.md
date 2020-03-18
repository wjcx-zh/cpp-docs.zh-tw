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
ms.openlocfilehash: 8323723f2049d3db469e874c91b99f4cfb561c72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439322"
---
# <a name="link-output"></a>LINK 輸出

連結輸出包含 .exe 檔案、Dll、對應檔和訊息。

##  <a name="_core_output_files"></a>輸出檔

連結的預設輸出檔案是 .exe 檔案。 如果指定[/DLL](dll-build-a-dll.md)選項，連結會建立 .dll 檔案。 您可以使用 [[輸出檔名稱] （/out）](out-output-file-name.md)選項來控制輸出檔的名稱。

在累加模式中，連結會建立 .ilk 檔案，以保存程式的後續累加組建的狀態資訊。 如需 .ilk 檔案的詳細資訊，請參閱[.ilk](dot-ilk-files-as-linker-input.md)檔案。 如需累加連結的詳細資訊，請參閱[漸進式連結（/INCREMENTAL）](incremental-link-incrementally.md)選項。

當連結建立包含匯出（通常是 DLL）的程式時，它也會建立 .lib 檔案，除非組建中使用了 .exp 檔案。 您可以使用[/IMPLIB](implib-name-import-library.md)選項來控制匯入程式庫檔案名。

如果指定了 [產生對應檔[（/MAP）](map-generate-mapfile.md) ] 選項，連結就會建立對應檔。

如果指定了 [[產生 Debug Info （/debug）](debug-generate-debug-info.md) ] 選項，LINK 會建立 PDB 以包含程式的偵錯工具資訊。

##  <a name="_core_other_output"></a>其他輸出

當您輸入 `link` 而不需要任何其他命令列輸入時，連結會顯示使用方式語句來摘要說明其選項。

連結會顯示著作權和版本訊息，並回應命令檔輸入，除非使用 [[隱藏啟始資訊（/nologo）](nologo-suppress-startup-banner-linker.md) ] 選項。

您可以使用 [[列印進度訊息（/verbose）](verbose-print-progress-messages.md) ] 選項來顯示有關組建的其他詳細資料。

連結會以 .LNK*nnnn*的形式發出錯誤和警告訊息。 LIB、DUMPBIN 和 EDITBIN 也會使用此錯誤前置詞和數位範圍。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
