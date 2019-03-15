---
title: /KEYCONTAINER (指定金鑰容器以簽署組件)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
ms.openlocfilehash: 96d2f5fed0e450224f82ee909cea9d56082505fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807841"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (指定金鑰容器以簽署組件)

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>引數

*name*<br/>
包含索引鍵的容器。 將字串放在雙引號 ("") 如果它包含空格。

## <a name="remarks"></a>備註

連結器所建立的已簽署的組件公開金鑰插入組件資訊清單，並使用私密金鑰簽署最終組件。 若要產生金鑰檔，請輸入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令列。 **sn-i**安裝至容器的金鑰組。

如果您使用編譯[/LN](ln-create-msil-module.md)，金鑰檔的名稱會保留在模組中並併入編譯透過包含的模組，明確參考的組件時所建立的組件[#using](../../preprocessor/hash-using-directive-cpp.md)，或當連結[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)。

您可以也將加密資訊傳遞給編譯器以[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)。 使用[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)要部分簽署組件。 請參閱[強式名稱組件 （組件簽署） (C + + /cli CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)如需有關簽署組件。

其他會影響產生組件連結器選項如下：

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

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
