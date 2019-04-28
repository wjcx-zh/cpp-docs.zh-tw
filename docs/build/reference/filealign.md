---
title: /FILEALIGN （對齊的區段中的檔案）
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: 43cfdd6efb163013d05877e91c8375eb592295a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271147"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN （對齊的區段中的檔案）

**/FILEALIGN**連結器選項可讓您指定輸出檔中寫入為指定大小的倍數的區段的對齊方式。

## <a name="syntax"></a>語法

> __/FILEALIGN:__*大小*

### <a name="parameters"></a>參數

*size*<br/>
區段的對齊大小位元組，這必須是 2 的乘冪。

## <a name="remarks"></a>備註

**/FILEALIGN**選項可讓連結器来對齊輸出檔案之倍數的界限上的每一節*大小*值。 根據預設，連結器不會使用固定的對齊方式的大小。

**/FILEALIGN**選項可用來提升磁碟使用率的效率，或將頁面從磁碟載入速度。 適用於針對較小的裝置，或保留較小的下載項目執行的應用程式時，可能較小的區段大小。 區段記憶體對齊在磁碟上的不會影響在記憶體中的對齊方式。

請使用 [DUMPBIN](dumpbin-reference.md) 來查看輸出檔案中區段的相關資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **命令列**中的屬性頁面**連結器**資料夾。

1. 輸入選項名稱 **/FILEALIGN:** 以及的大小**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
