---
title: /TLBOUT (命名 .TLB 檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 62913eaadd0f0a88f05ce347a6778062a1e66f17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509337"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (命名 .TLB 檔)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>引數

*path*<br/>
應在其中建立 .tlb 檔案的絕對或相對路徑規格。

*filename*<br/>
指定 MIDL 編譯器所建立之 .tlb 檔案的名稱。 未採用副檔名：如果您想要副檔名為 .tlb，請指定 *filename*。

## <a name="remarks"></a>備註

/TLBOUT 選項會指定 .tlb 檔案的名稱和副檔名。

連結具有 [module](../../windows/attributes/module-cpp.md) 屬性的專案時，MSVC 連結器會呼叫 MIDL 編譯器。

如果未指定/TLBOUT，.tlb 檔案將會從 [/IDLOUT](idlout-name-midl-output-files.md) *檔案名*取得其名稱。 如果未指定/IDLOUT，則會將 .tlb 檔案稱為 vc70 .tlb。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [ **內嵌 IDL** ] 屬性頁。

1. 修改 **類型程式庫** 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/IGNOREIDL (不會將屬性處理至 MIDL) ](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (指定 MIDL 命令列選項) ](midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/attributes/cpp-attributes-com-net.md)
