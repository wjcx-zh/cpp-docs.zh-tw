---
title: /LIBPATH (其他 Libpath)
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: ab586c788825a854e7d3cb3760da6e4e5558de3a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819879"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH (其他 Libpath)

```
/LIBPATH:dir
```

## <a name="parameters"></a>參數

*dir*<br/>
指定的路徑，連結器會先搜尋再搜尋 LIB 環境選項中指定的路徑。

## <a name="remarks"></a>備註

您可以使用 /LIBPATH 選項來覆寫環境程式庫路徑。 連結器會先搜尋此選項時，所指定路徑中，並再搜尋 LIB 環境變數中指定的路徑。 您可以指定您輸入每個 /LIBPATH 選項只能有一個目錄。 如果您想要指定多個目錄，您必須指定多個 /LIBPATH 選項。 連結器然後會在順序中，搜尋指定的目錄。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **一般**屬性頁。

1. 修改**其他程式庫目錄**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
