---
title: / SOURCELINK （包括 Sourcelink PDB 檔案）
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: 5c742a37803f450aa6084c862800583f70bcedde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480986"
---
# <a name="sourcelink-include-sourcelink-file-in-pdb"></a>/ SOURCELINK （包括 Sourcelink PDB 檔案）

指定要包含在連結器所產生的 PDB 檔案中的 SourceLink 組態檔。

## <a name="syntax"></a>語法

> **/ SOURCELINK:**_檔名_

## <a name="arguments"></a>引數

*filename*<br/>
指定的 JSON 格式組態檔，其中包含 url 的本機檔案路徑的簡單對應，可以擷取原始程式檔偵錯工具的顯示。 此檔案的格式資訊，請參閱[來源連結 JSON 結構描述](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema)。

## <a name="remarks"></a>備註

SourceLink 是語言和原始檔控制無從驗證的系統，可提供來源偵錯二進位檔。 原生 c + + 二進位檔從 Visual Studio 2017 版本 15.8 支援 SourceLink。 如需 SourceLink 的概觀，請參閱 <<c0> [ 來源連結](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md)。 如需如何在專案中使用 SourceLink 以及如何為您專案的一部分產生 SourceLink 檔案資訊，請參閱[使用 SourceLink](https://github.com/dotnet/sourcelink#using-sourcelink)。

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>若要在 Visual Studio 中設定 /SOURCELINK 連結器選項

1. 開啟**屬性頁**專案 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **命令列**屬性頁。

1. 在 **其他選項**方塊中，加入 **/SOURCELINK:**_檔名_，然後選擇  **確定**或**套用**以儲存變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 此選項並沒有對等的程式設計。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
