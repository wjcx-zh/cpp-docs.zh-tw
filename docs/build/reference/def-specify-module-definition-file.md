---
title: /DEF (指定模組定義檔)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: c08412fb50835485e7941b2bb1db088943387b71
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807438"
---
# <a name="def-specify-module-definition-file"></a>/DEF (指定模組定義檔)

```
/DEF:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
模組定義檔案 (.def) 傳遞至連結器的名稱。

## <a name="remarks"></a>備註

/DEF 選項會將模組定義檔 (.def) 傳遞給連結器。 只有一個.def 檔可以指定在連結上。 如需.def 檔的詳細資訊，請參閱[模組定義檔](module-definition-dot-def-files.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **輸入**屬性頁。

1. 修改**模組定義檔**屬性。

若要指定.def 檔從開發環境中的，您應該將它新增至專案及其他檔案，然後指定 /DEF 選項的檔案。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
