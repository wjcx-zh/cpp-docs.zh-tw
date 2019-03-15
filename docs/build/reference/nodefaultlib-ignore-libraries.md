---
title: /NODEFAULTLIB (忽略程式庫)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: cacc1ef312065da5d6e62ddba1040e87fae9d709
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807451"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (忽略程式庫)

```
/NODEFAULTLIB[:library]
```

## <a name="arguments"></a>引數

*library*<br/>
您想要略過 lib.exe 解析外部參考時，連結器程式庫。

## <a name="remarks"></a>備註

/NODEFAULTLIB 選項會告訴連結器解析外部參考時，它會搜尋程式庫清單中移除一或多個預設程式庫。

若要建立的.obj 檔案，不包含預設程式庫的參考，請使用[/Zl （省略預設程式庫名稱）](zl-omit-default-library-name.md)。

根據預設，/NODEFAULTLIB 從解析外部參考時，它會搜尋程式庫清單中移除所有預設程式庫。 選擇性*程式庫*參數可讓您解析外部參考時，它會搜尋程式庫清單中移除指定的程式庫或程式庫。 指定您想要排除的每個程式庫的一個 /NODEFAULTLIB 選項。

連結器會解析外部定義的參考，您明確指定，則程式庫 /DEFAULTLIB 選項中，以指定的預設程式庫中，然後再.obj 檔中所命名的預設程式庫，請搜尋第一次。

/NODEFAULTLIB:*程式庫*覆寫[/DEFAULTLIB:](defaultlib-specify-default-library.md)*文件庫*當相同*文件庫*中同時指定名稱。

如果您使用 /NODEFAULTLIB，比方說，若要建置您的程式不使用 C 執行階段程式庫中，您可能也使用[/ENTRY](entry-entry-point-symbol.md)在程式中指定的進入點 （函式）。 如需詳細資訊，請參閱 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **輸入**屬性頁。

1. 選取 **忽略所有預設程式庫**屬性，或指定您想要忽略中的程式庫的一份**忽略特定程式庫**屬性。 **命令列**屬性頁面會顯示您對這些屬性變更的影響。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
