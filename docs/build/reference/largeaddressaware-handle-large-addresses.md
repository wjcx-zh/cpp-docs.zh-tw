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
ms.openlocfilehash: 81a560ebf083e2f93d9bb514fc401186291d7f41
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808114"
---
# <a name="largeaddressaware-handle-large-addresses"></a>/LARGEADDRESSAWARE (處理大型記憶體位址)

```
/LARGEADDRESSAWARE[:NO]
```

## <a name="remarks"></a>備註

/LARGEADDRESSAWARE 選項會告訴連結器應用程式可以處理大於 2 gb 的位址。 在 64 位元編譯器中，依預設會啟用此選項。 在 32 位元編譯器中，如果連結器列未否則指定 /LARGEADDRESSAWARE，會啟用 /largeaddressaware: no。

如果應用程式已連結 /LARGEADDRESSAWARE，DUMPBIN [/HEADERS](headers.md)會顯示所造成影響的資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **系統**屬性頁。

1. 修改**啟用大型記憶體位址**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
