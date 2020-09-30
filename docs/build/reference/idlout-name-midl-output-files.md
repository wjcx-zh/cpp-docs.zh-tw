---
title: /IDLOUT (命名 MIDL 輸出檔)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 8dc26a0564a979c918d1eb1eb85e63e9c73caba0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506931"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (命名 MIDL 輸出檔)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>參數

*path*<br/>
絕對或相對路徑規格。 藉由指定路徑，您只會影響 .idl 檔的位置;所有其他檔案都放在專案目錄中。

*filename*<br/>
指定 MIDL 編譯器所建立的 .idl 檔名稱。 未採用副檔名：如果您想要副檔名為 .idl，請指定 *filename*。

## <a name="remarks"></a>備註

/IDLOUT 選項會指定 .idl 檔案的名稱和副檔名。

連結具有 [module](../../windows/attributes/module-cpp.md) 屬性的專案時，MSVC 連結器會呼叫 MIDL 編譯器。

/IDLOUT 也會指定與 MIDL 編譯器相關聯之其他輸出檔案的檔案名：

- *檔案名*.tlb

- *檔案名*_p。c

- *檔案名*_i。c

- *filename*。h

*filename* 是您傳遞給/IDLOUT. 的參數 如果指定 [/TLBOUT](tlbout-name-dot-tlb-file.md) ，則 .tlb 檔案將會從/TLBOUT *檔案名*取得其名稱。

如果您未指定/IDLOUT 或/TLBOUT，連結器將會建立 vc70 .tlb、vc70 .idl、vc70_p .c、vc70_i .c 和 vc70 .h。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [ **內嵌 IDL** ] 屬性頁。

1. 修改 [ **合併 IDL 基底檔案名** ] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/IGNOREIDL (不會將屬性處理至 MIDL) ](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (指定 MIDL 命令列選項) ](midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/attributes/cpp-attributes-com-net.md)
