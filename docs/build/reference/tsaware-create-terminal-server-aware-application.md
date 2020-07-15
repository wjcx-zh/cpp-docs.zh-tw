---
title: /TSAWARE (建立終端伺服器感知應用程式)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: 135d919278c8e969dc3a31381d5abbd1058c8663
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373888"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (建立終端伺服器感知應用程式)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>備註

/TSAWARE 選項會在程式映射的選擇性標頭的 [IMAGE_OPTIONAL_HEADER DllCharacteristics] 欄位中設定旗標。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。

當應用程式不是終端機伺服器感知（也稱為繼承應用程式）時，終端機伺服器會對繼承應用程式進行某些修改，使其在多使用者環境中能夠正常運作。 例如，終端機伺服器會建立虛擬 Windows 資料夾，讓每個使用者取得 Windows 資料夾，而不是取得系統的 Windows 目錄。 這可讓使用者存取自己的 INI 檔案。 此外，終端機伺服器會對繼承應用程式的登錄進行一些調整。 這些修改會使終端機伺服器上繼承應用程式的載入速度變慢。

如果應用程式是終端機伺服器感知，它就不能依賴 INI 檔案，也不能在安裝期間寫入**HKEY_CURRENT_USER**登錄。

如果您使用/TSAWARE，而您的應用程式仍然使用 INI 檔案，則系統的所有使用者都會共用這些檔案。 如果這是可接受的，您仍然可以使用/TSAWARE 連結應用程式;否則，您必須使用/TSAWARE： NO。

Windows 和主控台應用程式預設會啟用/TSAWARE 選項。 如需相關資訊，請參閱[/SUBSYSTEM](subsystem-specify-subsystem.md)和[/VERSION](version-version-information.md) 。

/TSAWARE 對驅動程式或 Dll 無效。

如果應用程式已與/TSAWARE 連結，DUMPBIN [/HEADERS](headers.md)會顯示該效果的資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [**系統**] 屬性頁。

1. 修改 [**終端機伺服器**] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜ <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A> ＞。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[儲存使用者特定資訊](/windows/win32/TermServ/storing-user-specific-information)<br/>
[終端機服務環境中的繼承應用程式](https://docs.microsoft.com/previous-versions//aa382957(v=vs.85))
