---
title: /OUT (輸出檔名稱)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812417"
---
# <a name="out-output-file-name"></a>/OUT (輸出檔名稱)

```
/OUT:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
使用者指定輸出檔名稱。 它會取代預設的名稱。

## <a name="remarks"></a>備註

/OUT 選項會覆寫預設名稱和連結器所建立的程式位置。

根據預設，連結器會形成使用指定的第一個.obj 檔案和適當的延伸模組 （.exe 或.dll） 的基底名稱的檔案名稱。

此選項的檔名或匯入程式庫的預設基底名稱。 如需詳細資訊，請參閱 <<c0> [ 產生對應檔](map-generate-mapfile.md)(/map) 和[/IMPLIB](implib-name-import-library.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **一般**屬性頁。

1. 修改**輸出檔**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
