---
title: /INTEGRITYCHECK (需要簽章檢查)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492839"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (需要簽章檢查)

指定在載入時, 必須檢查二進位影像的數位簽章。

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>備註

根據預設, **/INTEGRITYCHECK**為 off。

**/INTEGRITYCHECK**選項會設定在 DLL 檔案或可執行檔的 PE 標頭中, 這是記憶體管理員用來檢查數位簽章以在 Windows 中載入影像的旗標。 此選項必須針對32位和64位 Dll 設定, 以執行特定 Windows 功能載入的核心模式程式碼, 而且建議用於 Windows Vista、Windows 7、Windows 8、Windows Server 2008 和 Windows Server 2012 上的所有設備磁碟機。 Windows Vista 之前的 Windows 版本會忽略此旗標。 如需詳細資訊, 請參閱[可移植執行檔 (PE) 的強制完整性簽署](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 展開 [連結器] 節點。

1. 選取 [**命令列**] 屬性頁。

1. 在 [**其他選項**] `/INTEGRITYCHECK`中`/INTEGRITYCHECK:NO`, 輸入或。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)<br/>
[可移植執行檔 (PE) 的強制完整性簽署](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[核心模式程式碼簽署需求](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[Appinit.reg Dll 和安全開機](/windows/win32/dlls/secure-boot-and-appinit-dlls)
