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
ms.openlocfilehash: b21e8eb266de9a0baa0512a82acb0ae8a9f650a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500421"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (命名 MIDL 輸出檔)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>參數

*path*<br/>
絕對或相對路徑規格。 根據指定的路徑，會影響.idl 檔案; 的位置所有其他檔案位於專案目錄中。

*filename*<br/>
指定 MIDL 編譯器所建立的.idl 檔案的名稱。 沒有檔案延伸模組會假定;指定*filename*.idl，如果您想要的.idl 副檔名。

## <a name="remarks"></a>備註

/IDLOUT 選項會指定.idl 檔的副檔名與名稱。

連結有的專案時，將會呼叫 Visual c + + 連結器的 MIDL 編譯器[模組](../../windows/module-cpp.md)屬性。

/IDLOUT 也會指定其他 MIDL 編譯器與相關聯的輸出檔的檔案名稱：

- *檔名*.tlb

- *檔名*_p.c

- *檔名*_i.c

- *檔名*.h

*檔名*是您傳遞給 /IDLOUT 的參數。 如果[/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)會指定.tlb 檔會收到其名稱從 /TLBOUT *filename*。

如果您指定不 /IDLOUT，也不 /TLBOUT，連結器將建立 vc70.tlb、 vc70.idl、 vc70_p.c、 vc70_i.c 和 vc70.h。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **內嵌 IDL**屬性頁。

1. 修改**合併 IDL 主檔名**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (不要將屬性處理至 MIDL 中)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (指定 MIDL 命令列選項)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[建置屬性化程式](../../windows/building-an-attributed-program.md)