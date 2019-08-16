---
title: /ALLOWISOLATION (資訊清單查閱)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 7c799f3d44428643bccc2869255ffa4e9d194d70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493129"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (資訊清單查閱)

指定資訊清單查閱的行為。

## <a name="syntax"></a>語法

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>備註

**/ALLOWISOLATION: [否**] 表示載入 dll, 如同沒有資訊清單, 並使連結器在選擇性`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`標頭的`DllCharacteristics`欄位中設定位。

**/ALLOWISOLATION**會導致作業系統執行資訊清單查閱和載入。

**/ALLOWISOLATION**是預設值。

停用可執行檔的隔離時, Windows 載入器不會嘗試尋找新建立之進程的應用程式資訊清單。 新的進程將不會有預設啟用內容, 即使可執行檔中有資訊清單, 或將它放在與名稱<em>可執行檔</em>檔案名相同的目錄中。

如需詳細資訊, 請參閱[資訊清單檔案參考](/windows/win32/SbsCs/manifest-files-reference)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 [設定] [**屬性** > ] [**連結器** > **資訊清單**檔案] 屬性頁。

1. 修改 [**允許隔離**] 屬性。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
