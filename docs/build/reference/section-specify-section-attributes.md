---
title: "/SECTION （指定區段屬性） |Microsoft 文件"
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa214c7efeeee595300204df900a333258052772
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="section-specify-section-attributes"></a>/SECTION (指定區段屬性)

> **/SECTION:**_名稱_，[[**！**]{**DEKPRSW**}] [**，ALIGN =**_數目_]

## <a name="remarks"></a>備註

**/Section**選項變更的屬性區段中，覆寫設定編譯區段.obj 檔時的屬性。

A*區段*在可攜式執行檔 (PE) 檔案是包含程式碼或資料的記憶體將具名連續區塊。 某些章節包含程式碼或程式直接宣告和使用，而其他資料區段會為您建立由連結器和程式庫管理員 (lib.exe)，並包含作業系統内容的資訊的資料。 如需詳細資訊，請參閱[PE 格式](https://msdn.microsoft.com/library/windows/desktop/ms680547)。

指定冒號 （:） 和區段*名稱*。 *名稱*區分大小寫。

請勿下列名稱，因為它們與標準名稱衝突。 例如，.sdata RISC 平台上使用：

- .arch

- .bss

- .data

- .edata

- .idata

- .pdata

- .rdata

- .reloc

- .rsrc

- .sbss

- .sdata

- .srdata

- .text

- .xdata

指定一或多個區段的屬性。 下面列出的屬性字元不區分大小寫。 您必須指定您想要有; 區段的所有屬性省略的屬性字元會關閉該屬性位元。 如果您未指定 R、 W、 或 E，現有的讀取、 寫入或可執行檔的狀態維持不變。

要變換正負號的屬性，在之前它一個內含驚嘆號 （！） 的字元。 此表格顯示的屬性字元意義：

|字元|屬性|意義|
|---------------|---------------|-------------|
|E|執行|區段，則可執行檔|
|R|讀取|允許對於資料的讀取的作業|
|W|Write|允許對於資料的寫入作業|
|S|Shared|共用區段載入影像的所有處理程序|
|D|可捨棄|標記為可捨棄區段|
|K|快取|標記為不可快取區段|
|P|分頁|標記為不可分頁區段|

對應到它們的區段旗標都使用負的意義上，K 和 P 並不常見。 如果您指定其中一個在.text 區段使用**/SECTION:.text、 K**選項，沒有任何差異 > 一節旗標中的執行時[DUMPBIN](../../build/reference/dumpbin-options.md)與[/HEADERS](../../build/reference/headers.md)選項。一節已隱含已快取。 若要移除預設值，指定**/SECTION:.text，！K**改為。 DUMPBIN 顯示區段特性，包括 「 無法快取 」。

沒有 E、 R、 設定或 W PE 檔中的區段可能會無效。

**ALIGN =**_數目_引數可讓您指定的特定區段的對齊值。 _數目_引數是以位元組為單位，且必須是 2 的乘冪。 請參閱[/對齊](../../build/reference/align-section-alignment.md)如需詳細資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選擇**組態屬性** > **連結器** > **命令列**屬性頁。

1. 輸入中的選項**其他選項**方塊。 選擇**確定**或**套用**以套用變更。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)  
[連結器選項](../../build/reference/linker-options.md)  
