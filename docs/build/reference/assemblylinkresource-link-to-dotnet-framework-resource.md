---
title: /ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)
ms.date: 11/04/2016
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
ms.openlocfilehash: fb707a2721ed40ee3ec37d01b2bbcfcc51f05c38
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "57807802"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (連結到 .NET Framework 資源)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
您要從組件連結的目標 .NET Framework 資源檔。

## <a name="remarks"></a>備註

/ASSEMBLYLINKRESOURCE 選項會建立輸出檔案中的.NET Framework 資源的連結將資源檔不會放在輸出檔中。 [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)資源檔嵌入輸出檔。

連結的資源是公用的組件時使用連結器建立的。

/ASSEMBLYLINKRESOURCE 需要編譯，包括[/clr](clr-common-language-runtime-compilation.md);[/LN](ln-create-msil-module.md)或是[/NOASSEMBLY](noassembly-create-a-msil-module.md) /ASSEMBLYLINKRESOURCE 不允許。

如果*檔名*是.NET Framework 建立的資源檔，例如，藉由[Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)或在開發環境中，它可以存取使用中的成員**System.Resources**命名空間。 如需詳細資訊，請參閱 < [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager)。 如需其他資源，請使用**GetManifestResource** \*中的方法**System.Reflection.Assembly**類別，以在執行階段存取資源。

*檔名*可以是任何檔案格式。 例如，您可能要產生組件，原生 DLL 部分，以便將它安裝在全域組件快取，並從組件中的 managed 程式碼存取。

其他會影響產生組件連結器選項如下：

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入到選項**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
