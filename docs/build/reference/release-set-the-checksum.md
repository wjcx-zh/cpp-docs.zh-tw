---
title: /RELEASE (設定總和檢查碼)
ms.date: 11/04/2016
f1_keywords:
- /release
- VC.Project.VCLinkerTool.SetChecksum
helpviewer_keywords:
- -RELEASE linker option
- /RELEASE linker option
- checksum setting
- RELEASE linker option
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
ms.openlocfilehash: 1dc09b38beeb763733f8fa6a8ffa972059b30e03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318923"
---
# <a name="release-set-the-checksum"></a>/RELEASE (設定總和檢查碼)

```
/RELEASE
```

## <a name="remarks"></a>備註

/RELEASE 選項的.exe 檔的標頭中設定總和檢查碼。

作業系統的裝置驅動程式需要總和檢查碼。 設定的總和檢查碼的裝置驅動程式的發行版本以確保與未來的作業系統相容性。

/RELEASE 選項預設設定時[了](subsystem-specify-subsystem.md)指定選項。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 按一下 **連結器**資料夾。

1. 按一下 **進階**屬性頁。

1. 修改**設定的總和檢查碼**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
