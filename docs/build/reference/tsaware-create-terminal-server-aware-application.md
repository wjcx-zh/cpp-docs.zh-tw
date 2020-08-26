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
ms.openlocfilehash: c2ec12b0b5fbe241d75acc4bb0d87837371a293e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845727"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (建立終端伺服器感知應用程式)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>備註

/TSAWARE 選項會在程式映射的選用標頭的 IMAGE_OPTIONAL_HEADER DllCharacteristics] 欄位中設定旗標。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。

當應用程式不知道終端機伺服器 (也稱為繼承應用程式) ，終端機伺服器會對繼承應用程式進行某些修改，使其在多使用者環境中正常運作。 例如，終端機伺服器會建立虛擬 Windows 資料夾，讓每個使用者都取得 Windows 資料夾，而不是取得系統的 Windows 目錄。 這可讓使用者存取他們自己的 INI 檔案。 此外，終端機伺服器也會對繼承應用程式的登錄進行一些調整。 這些修改會使終端機伺服器上繼承應用程式的載入速度變慢。

如果應用程式是終端機伺服器感知，在安裝期間，它必須依賴 INI 檔案，也不會寫入 **HKEY_CURRENT_USER** 登錄。

如果您使用/TSAWARE，而您的應用程式仍使用 INI 檔案，則系統的所有使用者都會共用這些檔案。 如果是可接受的，您仍然可以將應用程式與/TSAWARE 連結。否則，您必須使用/TSAWARE： NO。

Windows 和主控台應用程式預設會啟用/TSAWARE 選項。 如需詳細資訊，請參閱 [/SUBSYSTEM](subsystem-specify-subsystem.md) 和 [/VERSION](version-version-information.md) 。

/TSAWARE 對驅動程式或 Dll 而言是不正確。

如果應用程式是與/TSAWARE 連結，DUMPBIN [/HEADERS](headers.md) 將會顯示該效果的資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] **** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [ **系統** ] 屬性頁。

1. 修改 **終端機伺服器** 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[儲存使用者特定資訊](/windows/win32/TermServ/storing-user-specific-information)<br/>
[終端機服務環境中的繼承應用程式](/previous-versions/aa382957(v=vs.85))
