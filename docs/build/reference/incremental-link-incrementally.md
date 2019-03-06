---
title: /INCREMENTAL (以累加方式連結)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 60cec41173afc9955bddf9df0bd6796b5df6285c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414079"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (以累加方式連結)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>備註

控制連結器處理累加連結的方式。

根據預設，連結器是以累加模式執行。 若要覆寫預設的累加連結，請指定 /INCREMENTAL:NO。

功能上相當於非累加方式連結的程式以累加方式連結的計劃。 不過，因為它已準備好後續累加連結，以累加方式連結的可執行檔、 靜態程式庫或動態連結程式庫檔案：

- 大於非累加方式連結的程式因為填補的程式碼和資料。 填補可以讓連結器增加函式和資料的大小不重新建立該檔案。

- 可能包含跳躍點 (Jump) Thunk，用以將函式重新配置到新的位址。

   > [!NOTE]
   > 若要確保您的最終版本組建不包含填補或 thunk，非累加方式連結您的程式。

若要在不考慮預設值的情況下以累加方式連結，請指定 /INCREMENTAL。 選取此選項時，連結器就會發出警告，如果它無法以累加連結，並接著非累加方式連結程式。 有些選項和情況會覆寫 /INCREMENTAL。

大部分程式都可以用累加方式連結。 然而，有些變更可能太大，而且有些選項與累加連結不相容。 如果指定了以下任何選項，LINK 便會執行完整連結：

- 未選取以累加方式連結 (/INCREMENTAL:NO)

- 選取 /OPT:REF

- 選取 /OPT:ICF

- 選取 /OPT:LBR

- 選取 /ORDER

/ 增量時就會隱含[/ 偵錯](../../build/reference/debug-generate-debug-info.md)指定。

此外，如果發生下列任何情況，LINK 也會執行完整連結：

- 找不到累加狀態檔 (.ilk)  (LINK 會為後續的累加連結建立新的 .ilk 檔)。

- 對 .ilk 檔沒有寫入權限  （LINK 會忽略.ilk 檔並且連結非以累加的方式。）

- 找不到 .exe 或 .dll 輸出檔。

- .ilk、.exe 或 .dll 的時間戳記已變更。

- 某個 LINK 選項已變更。 大部分 LINK 選項在不同組建之間有所變更時，都會產生完整連結。

- 加入或省略了某個目的檔 (.obj)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **連結器**資料夾。

1. 選取 [ **一般** ] 屬性頁。

1. 修改**啟用累加連結**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
