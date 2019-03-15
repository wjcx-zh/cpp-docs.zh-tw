---
title: /ASSEMBLYDEBUG (加入 DebuggableAttribute)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: b9899ea76b7a23a0d09442fca01e7d968c5e8aa6
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817617"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG (加入 DebuggableAttribute)

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ASSEMBLYDEBUG 會發出**DebuggableAttribute**屬性與偵錯資訊追蹤並停用 JIT 最佳化。 這是等同於來源中指定下列屬性：

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

/Assemblydebug: disable 會發出**DebuggableAttribute**屬性但停用偵錯資訊的追蹤，並啟用 JIT 最佳化。 這是等同於來源中指定下列屬性：

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

預設值將不會發出**DebuggableAttribute**屬性。

也可以直接在原始程式碼中的組件加入 DebuggableAttribute。 例如，套用至物件的

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>備註

必須明確指定的受控映像無法偵錯。 使用[/Zi](z7-zi-zi-debug-information-format.md)單獨不足夠。

其他會影響產生組件連結器選項如下：

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**偵錯的組件**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
