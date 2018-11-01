---
title: /VERSION (版本資訊)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 3e24a5307b8c4f60f29de390d38d9694f1cacf29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529685"
---
# <a name="version-version-information"></a>/VERSION (版本資訊)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>引數

*主要*和*次要*<br/>
您想要的.exe 或.dll 檔案的標頭中的版本號碼。

## <a name="remarks"></a>備註

/VERSION 選項會告訴連結器將版本號碼放入.exe 或.dll 檔案的標頭。 使用 DUMPBIN [/HEADERS](../../build/reference/headers.md)以查看映像版本欄位，選擇性的標頭值，以檢視 /VERSION 的效果。

*主要*並*次要*引數是介於 0 到 65535 的十進位數字。 預設值是版本 0.0。

以 /VERSION 指定的資訊不會影響您在檔案總管中檢視應用程式屬性時所顯示的版本資訊。 版本資訊來自於用來建置應用程式的資源檔。 請參閱[版本資訊編輯器](../../windows/version-information-editor.md)如需詳細資訊。

若要插入的版本號碼的另一個方法是使用[版本](../../build/reference/version-c-cpp.md)模組定義陳述式。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **一般**屬性頁。

1. 修改**版本**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)