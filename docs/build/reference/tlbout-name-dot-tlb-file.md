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
ms.openlocfilehash: 4e04514933a521bbf9d927fa6b47bacb87896353
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822258"
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

連結有的專案時，將會呼叫 MSVC 連結器的 MIDL 編譯器[模組](../../windows/module-cpp.md)屬性。

如果未指定 /TLBOUT，.tlb 檔案會從其名稱[/IDLOUT](idlout-name-midl-output-files.md) *filename*。 如果未指定 /IDLOUT，.tlb 檔就會呼叫 vc70.tlb。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **內嵌 IDL**屬性頁。

1. 修改**型別程式庫**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[/IGNOREIDL (不要將屬性處理至 MIDL 中)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (指定 MIDL 命令列選項)](midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/building-an-attributed-program.md)
