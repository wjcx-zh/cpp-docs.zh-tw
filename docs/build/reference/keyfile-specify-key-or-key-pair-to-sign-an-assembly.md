---
title: /KEYFILE (指定金鑰或金鑰組以簽署組件)
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: d309390c1ac1a19d9d4a982908dbbbac0bd52714
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813769"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (指定金鑰或金鑰組以簽署組件)

```
/KEYFILE:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
包含索引鍵的檔案。 將字串放在雙引號 ("") 如果它包含空格。

## <a name="remarks"></a>備註

連結器將公開金鑰插入到組件資訊清單，然後使用私密金鑰簽署最終組件。 若要產生金鑰檔，請輸入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令列。 簽署的組件即具有強式名稱。

如果您使用編譯[/LN](ln-create-msil-module.md)，金鑰檔的名稱會保留在模組中並併入編譯透過包含的模組，明確參考的組件時所建立的組件[#using](../../preprocessor/hash-using-directive-cpp.md)，或當連結[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)。

您可以也將加密資訊傳遞給使用連結器[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)。 使用[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)要部分簽署組件。 請參閱[強式名稱組件 （組件簽署） (C + + /cli CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)如需有關簽署組件。

在案例中都 **/KEYFILE**並 **/KEYCONTAINER**指定連結器 （藉由命令列選項或是自訂屬性），會先嘗試使用金鑰容器。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。 如果連結器找不到金鑰容器，它會嘗試使用以 /KEYFILE 指定的檔案。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件，並將金鑰資訊安裝在金鑰容器中 (類似於 sn -i)，這樣在下次編譯時，金鑰容器就會是有效的。

請注意，金鑰檔可能只包含公開金鑰。

請參閱[建立和使用強式名稱組件](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)如需有關簽署組件。

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
