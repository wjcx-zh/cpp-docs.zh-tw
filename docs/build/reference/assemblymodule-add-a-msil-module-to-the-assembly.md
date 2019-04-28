---
title: /ASSEMBLYMODULE (將 MSIL 模組加入組件)
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: 728e8a84ff8d1afac99f99dbb975c7fd9360bcc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273011"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE (將 MSIL 模組加入組件)

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
想要包含在這個組件中的模組。

## <a name="remarks"></a>備註

/ASSEMBLYMODULE 選項可讓您新增組件的模組參考。 在模組中的類型資訊將無法使用新增的模組參考的組件程式。 不過，在模組中的型別資訊可參考的組件的任何程式。

使用[#using](../../preprocessor/hash-using-directive-cpp.md)加入組件的模組參考和組件程式提供模組的類型資訊。

例如，請考慮下列案例：

1. 建立同名的模組[/LN](ln-create-msil-module.md)。

1. 使用不同的專案中的 /ASSEMBLYMODULE，要包含在目前的編譯中，將會建立組件的模組。 此專案不會參照的模組`#using`。

1. 任何參考這個組件的專案現在也可以使用從模組的類型。

其他會影響產生組件連結器選項如下：

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

MSVC 連結器接受.netmodule 檔做為輸入，因此，連結器產生的輸出檔的組件或.netmodule 任何連結器輸入.netmodule 沒有執行階段相依性。  如需詳細資訊，請參閱 [.netmodule 檔作為連結器輸入](netmodule-files-as-linker-input.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 **連結器**資料夾。

1. 按一下 **輸入**屬性頁。

1. 修改**將模組加入組件**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
