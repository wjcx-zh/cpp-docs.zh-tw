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
ms.openlocfilehash: fe76e0d40a2a19a002136a7e095875ad2903d434
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818449"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (資訊清單查閱)

指定資訊清單查閱的行為。

## <a name="syntax"></a>語法

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>備註

**/ALLOWISOLATION:NO**表示會載入 Dll，如同沒有任何資訊清單，並造成設定連結器`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`選擇性標頭的位元`DllCharacteristics`欄位。

**/ALLOWISOLATION**會導致作業系統查閱和載入資訊清單。

**/ALLOWISOLATION**是預設值。

可執行檔停用隔離時，Windows 載入器並不會嘗試尋找新建立的程序中的應用程式資訊清單。 新的處理序不會預設啟用的內容，即使有未在可執行檔或放在與名稱的可執行檔相同的目錄中的 資訊清單<em>可執行檔名稱</em>**.exe.manifest**。

如需詳細資訊，請參閱 <<c0> [ 資訊清單檔案參考](/windows/desktop/SbsCs/manifest-files-reference)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **資訊清單檔案**屬性頁。

1. 修改**允許隔離**屬性。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
