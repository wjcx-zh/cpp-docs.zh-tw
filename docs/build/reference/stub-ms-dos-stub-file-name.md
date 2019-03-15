---
title: /STUB (MS-DOS Stub 檔名)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: 7150d4ff8f35b00d96caa21fd5ea3754fec76030
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822401"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (MS-DOS Stub 檔名)

```
/STUB:filename
```

## <a name="arguments"></a>引數

*filename*<br/>
MS-DOS 應用程式。

## <a name="remarks"></a>備註

/STUB 選項會將 MS-DOS stub 程式附加至 Win32 程式。

如果在 MS-DOS 會執行檔案，則會叫用 stub 的程式。 它通常會顯示適當的訊息;不過，任何有效的 MS-DOS 應用程式可以是虛設常式程式。

指定*filename*虛設常式程式命令列上的冒號 （:） 之後。 連結器檢查*filename*並發出錯誤訊息，如果檔案不是可執行檔。 該程式必須是.exe 檔案;無效的 stub 程式.com 檔案。

如果未使用此選項，連結器會將發出下列訊息的預設 stub 程式附加：

```
This program cannot be run in MS-DOS mode.
```

建立虛擬裝置驅動程式時*filename*可讓使用者指定檔案名稱包含 （定義於 WINNT IMAGE_DOS_HEADER 結構。H) 用於 VXD，而不是預設標頭。

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
