---
title: /DELAYSIGN (部分簽署組件)
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 233a41a3e55ff2726712541b0af9db1f5e55eb56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435616"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (部分簽署組件)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>引數

**否**<br/>
指定組件不應該部分的簽署。

## <a name="remarks"></a>備註

使用 **/DELAYSIGN**如果您只想要的公開金鑰置於組件。 預設值是 **/delaysign: no**。

**/DELAYSIGN**選項沒有任何作用，除非搭配[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)或是[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)。

當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。 所產生的數位簽章會儲存在包含資訊清單的檔案中。 延遲簽署組件時，連結器不會計算和簽章，但保留空間儲存在檔案中，以便可以稍後再加入簽章。

例如，使用 **/DELAYSIGN**可讓測試人員將組件放在全域快取中。 測試之後，您可以將私密金鑰放在組件中，完整簽署組件。

請參閱[強式名稱組件 （組件簽署） (C + + /cli CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)並[Delay Signing an Assembly](/dotnet/framework/app-domains/delay-sign-assembly)如需有關簽署組件。

其他會影響產生組件連結器選項如下：

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入到選項**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)