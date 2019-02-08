---
title: 可編輯的檔案類型的資源 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: c40f9204-f2f2-400b-9f53-53b7bf291356
ms.openlocfilehash: 9f688c144a3453c2de849b36f34f6a465e3dfeae
ms.sourcegitcommit: 5a7dbd640376e13379f5d5b2cf66c4842e5e737b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55905715"
---
# <a name="editable-file-types-for-resources-c"></a>可編輯的檔案類型的資源 （c + +）

您可以開啟下列類型的檔案，並編輯所包含的資源。

|檔案名稱|描述|
|---------------|-----------------|
|.rc|資源指令碼檔。|
|.rct|資源範本檔。|
|.res|資源檔。|
|.resx|Managed 資源檔。|
|.exe|可執行檔。|
|.dll|動態連結程式庫檔案。|
|.bmp、.ico、.dib 和 .cur|點陣圖、圖示、工具列和游標檔案。|

## <a name="files-affected-by-resource-editing"></a>受資源編輯影響的檔案

Visual Studio 環境會在您的資源編輯工作階段期間使用下表中顯示的檔案。

|檔案名稱|描述|
|---------------|-----------------|
|偵錯工具|開發環境所產生的標頭檔；包含符號定義。 （原始檔控制中包含此檔案）。|
|Filename.aps|目前資源指令碼檔的二進位版本；用於快速載入。<br /><br /> 資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 (例如註解)。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。 （一般而言，您不能包含.aps 檔在原始檔控制中。）|
|.rc|包含目前專案中的資源所適用之指令碼的資源指令碼檔。 .aps 檔會在您每次存檔時覆寫此檔案。 （原始檔控制中包含此檔案）。|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源檔](../windows/resource-files-visual-studio.md)