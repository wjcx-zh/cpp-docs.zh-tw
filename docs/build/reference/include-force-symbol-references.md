---
title: /INCLUDE (強制符號參考)
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 389bd16829c2466b02cb879c8bc8d43c9efa6fb4
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421216"
---
# <a name="include-force-symbol-references"></a>/INCLUDE (強制符號參考)

```
/INCLUDE:symbol
```

## <a name="parameters"></a>參數

*symbol*<br/>
指定要加入至符號表中的符號。

## <a name="remarks"></a>備註

/INCLUDE 選項會告訴連結器，以指定的符號加入符號表。

若要指定多個符號，輸入逗號 （，）、 分號 （;） 或符號名稱之間保留一個空格。 在命令列中，可以指定 /INCLUDE:`symbol`一次，每個符號。

連結器解析`symbol`加上包含程式的符號定義的物件。 這項功能可用於包含的程式庫物件，否則就不會將連結到該程式。

指定符號使用此選項會覆寫該符號的移除[/opt: ref](../../build/reference/opt-optimizations.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **輸入**屬性頁。

1. 修改**強制符號參考**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
