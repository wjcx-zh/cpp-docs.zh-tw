---
title: /ASSEMBLYRESOURCE (內嵌 Managed 資源)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: 1eac489ffd01f6bd79fc8c5bbda23adb751c9486
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822648"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (內嵌 Managed 資源)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>參數

*filename*<br/>
您想要在這個組件中內嵌 managed 的資源。

*name*<br/>
選擇性。 資源; 的邏輯名稱用來載入資源的名稱。 預設值是檔案的名稱。

（選擇性） 您可以指定是否該檔案應為私用組件資訊清單中。 根據預設，*名稱*是公用的組件中。

## <a name="remarks"></a>備註

使用與 /ASSEMBLYRESOURCE 選項可內嵌在組件中的資源。

資源是公用的組件時使用連結器建立的。 連結器不允許您重新命名的組件中的資源。

如果*檔名*是.NET Framework 資源 (.resources) 建立的檔案，例如，藉由[資源檔產生器 (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator)或在開發環境中，它可以存取使用中的成員**System.Resources**命名空間 (請參閱[System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager)如需詳細資訊)。 如需其他資源，請使用**GetManifestResource** \*中的方法**System.Reflection.Assembly**類別，以在執行階段存取資源。

其他會影響產生組件連結器選項如下：

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **輸入**屬性頁。

1. 修改**嵌入 Managed 資源檔**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
