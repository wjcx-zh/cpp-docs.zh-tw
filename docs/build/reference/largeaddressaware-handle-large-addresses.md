---
title: /LARGEADDRESSAWARE (處理大型記憶體位址)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.LargeAddressAware
- /largeaddressaware
helpviewer_keywords:
- LARGEADDRESSAWARE linker option
- -LARGEADDRESSAWARE linker option
- /LARGEADDRESSAWARE linker option
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
ms.openlocfilehash: 6a83ac89c6ddf14885107193b32d9b7fe7853659
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543048"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (處理大型記憶體位址)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>備註

/LARGEADDRESSAWARE 選項會告訴連結器應用程式可以處理大於 2 gb 的位址。 在 64 位元編譯器中，依預設會啟用此選項。 在 32 位元編譯器中，如果連結器列未否則指定 /LARGEADDRESSAWARE，會啟用 /largeaddressaware: no。

如果應用程式已連結 /LARGEADDRESSAWARE，DUMPBIN [/HEADERS](../../build/reference/headers.md)會顯示所造成影響的資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **系統**屬性頁。

1. 修改**啟用大型記憶體位址**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)