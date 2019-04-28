---
title: /FIXED (固定基底位址)
ms.date: 11/04/2016
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
ms.openlocfilehash: 6cc89df76e48ee258a7c6608aab12573ab11729b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292480"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (固定基底位址)

```
/FIXED[:NO]
```

## <a name="remarks"></a>備註

告知作業系統只載入位於慣用基底位址的程式。 如果無法使用慣用的基底位址，作業系統就不會載入檔案。 如需詳細資訊，請參閱 [/BASE (基底位址)](base-base-address.md)。

/FIXED:NO 是 DLL 的預設值，而 /FIXED 則是其他專案類型的預設值。

/Fixed 則指定時，則連結不會產生重新配置區段的程式。 在執行階段時，如果作業系統無法在指定的位址載入程式，它便會發出錯誤訊息而且不會載入程式。

指定要在程式內產生重新配置區段的 /fixed: no。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **連結器**資料夾。

1. 選取 **命令列**屬性頁。

1. 輸入選項名稱，並在設定**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
