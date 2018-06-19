---
title: LINK 輸出 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae68de707ece35825a32a404ce14032d4bbd3141
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376724"
---
# <a name="link-output"></a>LINK 輸出
Link 輸出包含.exe 檔、 Dll、 對應檔，以及訊息。  
  
##  <a name="_core_output_files"></a> 輸出檔  
 連結的預設輸出檔案是.exe 檔案。 如果[/DLL](../../build/reference/dll-build-a-dll.md)指定選項時，連結會建置.dll 檔。 您可以控制在輸出檔名[輸出檔名稱 (/out)](../../build/reference/out-output-file-name.md)選項。  
  
 在累加模式中，連結會建立.ilk 檔，以保存程式的後續累加組建狀態資訊。 如需有關.ilk 檔的詳細資訊，請參閱[.ilk 檔](../../build/reference/dot-ilk-files-as-linker-input.md)。 如需有關累加連結的詳細資訊，請參閱[累加連結 (/incremental)](../../build/reference/incremental-link-incrementally.md)選項。  
  
 當連結建立程式，其中包含匯出 (通常是 DLL)，它也會建置.lib 檔案，除非在組建中使用.exp 檔案。 您可以控制在匯入程式庫檔名[/IMPLIB](../../build/reference/implib-name-import-library.md)選項。  
  
 如果[產生對應檔 (/map)](../../build/reference/map-generate-mapfile.md)指定選項時，連結會建立對應檔。  
  
 如果[產生偵錯資訊 (/debug)](../../build/reference/debug-generate-debug-info.md)指定選項時，連結會建立包含程式的偵錯資訊的 PDB。  
  
##  <a name="_core_other_output"></a> 其他輸出  
 當您輸入`link`沒有命令列的輸入，連結會顯示摘要其選項的使用方式陳述式。  
  
 連結會顯示著作權和版本的訊息和回應命令檔輸入，除非[隱藏程式啟始資訊 (/ NOLOGO)](../../build/reference/nologo-suppress-startup-banner-linker.md)選項使用。  
  
 您可以使用[列印進度訊息 (/verbose)](../../build/reference/verbose-print-progress-messages.md)選項可顯示有關組建的其他詳細資料。  
  
 連結會發出錯誤和警告訊息的形式 LNK*nnnn*。 這個錯誤前置字元和數字範圍也會使用 LIB、 DUMPBIN 和 EDITBIN。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)