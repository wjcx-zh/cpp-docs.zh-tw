---
title: /NOENTRY (沒有進入點)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
ms.openlocfilehash: fef4340fa4bb130ac54f4d5e66d4cd4d2f2a3049
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607359"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (沒有進入點)

```
/NOENTRY
```

## <a name="remarks"></a>備註

必須有 /NOENTRY 選項才能建立不包含可執行程式碼的僅含資源的 DLL。 如需詳細資訊，請參閱 <<c0> [ 建立 Resource-Only DLL](../../build/creating-a-resource-only-dll.md)。

使用此選項可防止 LINK 將 `_main` 的參考連結到 DLL 中。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取 **進階**屬性頁。

1. 修改**沒有進入點**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>。

## <a name="see-also"></a>另請參閱

[建立僅含資源的 DLL](../../build/creating-a-resource-only-dll.md)<br/>
[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)