---
title: /MANIFESTFILE (為資訊清單檔案命名)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ManifestFile
helpviewer_keywords:
- MANIFESTFILE linker option
- -MANIFESTFILE linker option
- /MANIFESTFILE linker option
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
ms.openlocfilehash: e75c6d8171aae22312ba6aaa2d4304d831ec6d0f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813834"
---
# <a name="manifestfile-name-manifest-file"></a>/MANIFESTFILE (為資訊清單檔案命名)

```
/MANIFESTFILE:filename
```

## <a name="remarks"></a>備註

/MANIFESTFILE 可讓您變更資訊清單檔案的預設名稱。  資訊清單檔案的預設名稱是副檔名為.manifest 的檔案名稱。

/MANIFESTFILE 會有任何作用，如果您沒有也連結[/manifest](manifest-create-side-by-side-assembly-manifest.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **資訊清單檔案**屬性頁。

1. 修改**資訊清單檔案**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
