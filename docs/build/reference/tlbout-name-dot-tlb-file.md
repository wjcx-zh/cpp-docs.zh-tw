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
ms.openlocfilehash: 3eaf4305c58ca70619e032f80e661b9c768f7813
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425519"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (命名 .TLB 檔)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>引數

*path*<br/>
應該在其中建立.tlb 檔案的絕對或相對路徑規格。

*filename*<br/>
指定 MIDL 編譯器所建立的.tlb 檔案的名稱。 沒有檔案延伸模組會假定;指定*filename*.tlb，如果您想.tlb 副檔名。

## <a name="remarks"></a>備註

/TLBOUT 選項會指定.tlb 檔案的副檔名與名稱。

連結有的專案時，將會呼叫 Visual c + + 連結器的 MIDL 編譯器[模組](../../windows/module-cpp.md)屬性。

如果未指定 /TLBOUT，.tlb 檔案會從其名稱[/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*。 如果未指定 /IDLOUT，.tlb 檔就會呼叫 vc70.tlb。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **內嵌 IDL**屬性頁。

1. 修改**型別程式庫**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (不要將屬性處理至 MIDL 中)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (指定 MIDL 命令列選項)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/building-an-attributed-program.md)
