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
ms.openlocfilehash: f6ed6184f8ae4b3a0f9db3c1f962a2918a185138
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816941"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (建立終端伺服器感知應用程式)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>備註

/TSAWARE 選項會設定旗標，在程式映像的選擇性標頭的 IMAGE_OPTIONAL_HEADER DllCharacteristics 欄位中。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。

當應用程式不是終端伺服器感知 （也就是舊版應用程式） 時，終端機伺服器會讓某些修改舊版的應用程式，以讓它在多使用者環境中正常運作。 比方說，終端機伺服器將會建立虛擬 Windows 資料夾中，使每個使用者取得 Windows 資料夾，而不是取得系統的 Windows 目錄。 這可讓使用者存取他們自己的 INI 檔案。 此外，終端機伺服器可讓舊版應用程式的登錄一些調整。 這些修改會減慢終端機伺服器上的舊版應用程式載入。

如果終端伺服器感知應用程式，它必須不依賴 INI 檔案也不寫入**HKEY_CURRENT_USER**在安裝期間登錄。

如果您使用 /TSAWARE，而且您的應用程式仍會使用的 INI 檔案，檔案會共用系統的所有使用者。 如果是可接受，您仍然可以連結 /TSAWARE; 您的應用程式否則，您必須使用 /tsaware: no。

/TSAWARE 選項會預設啟用 Windows 和主控台應用程式。 請參閱[/SUBSYSTEM](subsystem-specify-subsystem.md)並[/VERSION](version-version-information.md)的資訊。

/TSAWARE 不正確的驅動程式、 Vxd 或 Dll。

如果應用程式已連結 /TSAWARE，DUMPBIN [/HEADERS](headers.md)會顯示所造成影響的資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **系統**屬性頁。

1. 修改**終端機伺服器**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[儲存使用者專屬資訊](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[在終端機服務環境中的舊版應用程式](https://msdn.microsoft.com/library/aa382957.aspx)
