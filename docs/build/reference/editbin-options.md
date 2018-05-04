---
title: EDITBIN 選項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1922e410b0151337ce403e24d20ae90b7e964cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="editbin-options"></a>EDITBIN 選項
您可以使用 EDITBIN 來修改物件的檔案、 可執行檔，以及動態連結程式庫 (Dll)。 選項會指定 EDITBIN 所做的變更。  
  
 選項包含選項規範，這是虛線 （-） 或斜線 （/），後面接著選項的名稱。 選項名稱不能為縮寫。 某些選項可接受於冒號 ( : ) 之後指定的引數。 選項規格內允許任何空格或定位字元。 使用一個或多個空格或定位字元分隔命令列上的選項規格。 選項名稱及其關鍵字引數或檔名引數不區分大小寫。 例如，-bind 和 /BIND 意義相同。  
  
 EDITBIN 具有下列選項：  
  
|選項|用途|  
|------------|-------------|  
|[/ALLOWBIND](../../build/reference/allowbind.md)|指定 DLL 是否可以繫結。|  
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|指定 DLL 或可執行檔資訊清單查閱行為。|  
|[/APPCONTAINER](../../build/reference/appcontainer.md)|指定是否必須在 AppContainer 中執行應用程式 — 例如，UWP 應用程式。|  
|[/BIND](../../build/reference/bind.md)|在指定的物件中設定進入點位址，以加速載入時間。|  
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|指定 DLL 或可執行映像是否可以使用位址空間配置隨機載入 (ASLR) 功能，於載入時隨機重訂基底。|  
|[/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|向 Microsoft 報告內部錯誤。|  
|[/HEAP](../../build/reference/heap.md)|設定可執行映像的堆積大小 (位元組)。|  
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|指定 DLL 或可執行映像是否支援高熵 (64 位元) 位址空間配置隨機載入 (ASLR)。|  
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|指定是否在載入時間檢查數位簽章。|  
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|指定物件是否支援大於 2 GB 的位址。|  
|[/NOLOGO](../../build/reference/nologo-editbin.md)|隱藏 EDITBIN 程式啟始資訊。|  
|[/NXCOMPAT](../../build/reference/nxcompat.md)|指定可執行映像是否與 Windows 資料執行防止功能相容。|  
|[/REBASE](../../build/reference/rebase.md)|設定指定之物件的基底位址。|  
|[/RELEASE](../../build/reference/release.md)|在標頭中設定總和檢查碼。|  
|[/ 區段](../../build/reference/section-editbin.md)|覆寫區段的屬性。|  
|[/STACK](../../build/reference/stack.md)|設定可執行映像的堆疊大小 (位元組)。|  
|[/SUBSYSTEM](../../build/reference/subsystem.md)|指定執行環境。|  
|[/SWAPRUN](../../build/reference/swaprun.md)|指定可執行映像必須複製到分頁檔，再從分頁檔執行映像。|  
|[/TSAWARE](../../build/reference/tsaware.md)|指定應用程式是設計成在多使用者環境中執行。|  
|[/VERSION](../../build/reference/version.md)|在標頭中設定版本號碼。|  
  
## <a name="see-also"></a>另請參閱  
 [C/c + + 建置工具](../../build/reference/c-cpp-build-tools.md)   
 [EDITBIN 參考](../../build/reference/editbin-reference.md)