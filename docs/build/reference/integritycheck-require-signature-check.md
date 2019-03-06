---
title: /INTEGRITYCHECK (需要簽章檢查)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: ad4420847be7c8bbcaa9fda4c5b7dfda818e7f27
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419593"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (需要簽章檢查)

指定必須檢查在載入時間的二進位檔映像的數位簽章。

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>備註

根據預設， **/INTEGRITYCHECK**已關閉。

**/INTEGRITYCHECK**選項集 — DLL 或可執行檔的 PE 標頭中，記憶體管理員檢查數位簽章，以將影像載入 Windows 中的旗標。 這個選項必須設定適用於 32 位元和 64 位元 Dll 實作特定 Windows 功能中，載入的核心模式程式碼，並建議用於在 Windows Vista、 Windows 7、windows 8、windows、 Windows Server 2008 和 Windows Server 2012 的所有裝置驅動程式。 在 Windows Vista 之前的 Windows 版本會忽略此旗標。 如需詳細資訊，請參閱 <<c0> [ 強制完整性簽署的可攜式執行檔 (PE) 檔案](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **命令列**屬性頁。

1. 在 **其他選項**，輸入`/INTEGRITYCHECK`或`/INTEGRITYCHECK:NO`。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)<br/>
[強制的完整性簽署的可攜式執行檔 (PE) 檔案](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[核心模式程式碼簽署逐步解說](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[Windows 7 和 Windows Server 2008 中的 AppInit Dll](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)
