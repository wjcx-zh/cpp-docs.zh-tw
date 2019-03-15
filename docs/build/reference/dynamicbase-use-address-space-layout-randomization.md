---
title: /DYNAMICBASE (使用位址空間隨機載入)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: a3495de3ec72bcac78cdee2f5f3265864e7a2932
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807750"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (使用位址空間隨機載入)

指定是否要產生可執行映像可以隨機重定基底在載入時所使用的第一次在 Windows Vista 中可用的 Windows 位址空間配置隨機載入 (ASLR) 功能。

## <a name="syntax"></a>語法

> **/DYNAMICBASE**[**:NO**]

## <a name="remarks"></a>備註

**/DYNAMICBASE**選項會修改的標頭*可執行映像*，.dll 或.exe 檔案，以指出是否應該隨機重定基底在載入期間，應用程式，並可讓虛擬位址配置隨機載入，這會影響之虛擬記憶體位置的堆積，堆疊和其他作業系統配置。 **/DYNAMICBASE**選項適用於 32 位元和 64 位元的映像。 Windows Vista 和更新版本的作業系統上可支援 ASLR。 選項會忽略先前的作業系統。

根據預設， **/DYNAMICBASE**已啟用。 若要停用此選項，請使用 **/dynamicbase: no**。 **/DYNAMICBASE**選項是為了[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)選項影響。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **進階**屬性頁。

1. 修改**隨機化的基底位址**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Windows ISV 軟體安全性防禦措施](https://msdn.microsoft.com/library/bb430720.aspx)