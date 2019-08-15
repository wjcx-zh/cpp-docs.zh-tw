---
title: /SECTION (指定區段屬性)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 0a52e9c9dcd53b01f17dc36825732b34771c75bb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492633"
---
# <a name="section-specify-section-attributes"></a>/SECTION (指定區段屬性)

> **/SECTION:** _名稱_、[ **!** ]{**DEKPRSW**}][ **, 對齊 =** _數位_]

## <a name="remarks"></a>備註

**/SECTION**選項會變更區段的屬性, 並覆寫在編譯區段的 .obj 檔案時所設定的屬性。

可移植執行檔 (PE) 中的*區段*是名為連續的記憶體區塊, 其中包含程式碼或資料。 某些區段包含程式所宣告並直接使用的程式碼或資料, 而連結器和程式庫管理員 (lib) 會為您建立其他資料區段, 並包含作業系統的重要資訊。 如需詳細資訊, 請參閱[PE 格式](/windows/win32/Debug/pe-format)。

指定冒號 (:)和區段*名稱*。 *名稱*區分大小寫。

請勿使用下列名稱, 因為它們與標準名稱衝突。 例如, 在 RISC 平臺上使用 .sdata:

- 。

- .bss

- 。資料

- .edata

- .idata

- .pdata

- . .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

指定區段的一個或多個屬性。 下面所列的屬性字元並不區分大小寫。 您必須指定要讓區段擁有的所有屬性;省略的屬性字元會導致關閉該屬性位。 如果您未指定 R、W 或 E, 現有的讀取、寫入或可執行檔狀態會維持不變。

若要否定屬性, 請在其字元前面加上驚嘆號 (!)。 屬性字元的意義如下表所示:

|字元|屬性|意義|
|---------------|---------------|-------------|
|E|執行|區段是可執行檔|
|R|讀取|允許對資料進行讀取作業|
|W|Write|允許對資料進行寫入作業|
|S|Shared|在所有載入影像的進程之間共用區段|
|D|可捨棄|將區段標記為可捨棄|
|K|高速|將區段標記為不可快取|
|P|一部分|將區段標記為不可分頁|

K 和 P 不尋常, 其對應的區段旗標會用於負意義。 如果您使用 **/SECTION:. text, K**選項在. text 區段上指定其中一個專案, 當您使用[/HEADERS](headers.md)選項執行[DUMPBIN](dumpbin-options.md)時, 區段旗標中並沒有任何差異;區段已經隱含快取。 若要移除預設值, 請指定 **/SECTION:. text,!** 改為 K。 DUMPBIN 會顯示區段特性, 包括「未快取」。

PE 檔案中沒有 E、R 或 W 集的區段可能無效。

**ALIGN =** _number_引數可讓您指定特定區段的對齊值。 _Number_引數是以位元組為單位, 而且必須是2的乘冪。 如需詳細資訊, 請參閱[/align](align-section-alignment.md) 。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選擇 [設定] [**屬性** > ] [**連結器** > **命令列**] 屬性頁。

1. 在 [**其他選項**] 方塊中, 輸入選項。 選擇 **[確定]** 或 [套用] 以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
