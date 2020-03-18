---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438909"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>備註

此選項會變更區段的屬性，並覆寫在編譯或連結區段的目的檔時所設定的屬性。

在冒號（ **：** ）之後，指定區段的*名稱*。 若要變更區段名稱，請在 [*名稱*] 後面加上等號（=）和 [ *newname* ] 做為區段。

若要設定或變更區段的 `attributes`，請指定一個逗號（ **，** ），後面接著一或多個屬性字元。 若要否定屬性，請在其字元前面加上驚嘆號（！）。 下列字元會指定記憶體屬性：

|屬性|設定|
|---------------|-------------|
|c|代碼|
|d|可捨棄|
|e|可執行檔 (executable)|
|i|初始化的資料|
|k|快取的虛擬記憶體|
|m|連結移除|
|o|連結資訊|
|p|分頁虛擬記憶體|
|r|讀取|
|s|shared|
|u|未初始化的資料|
|w|寫入|

若要控制*對齊*，請指定後面接著下列其中一個字元的字元**A** ，以設定對齊的大小（以位元組為單位），如下所示：

|字元|對齊大小（位元組）|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|沒有對齊|

將 `attributes` 和*對齊*字元指定為不含空格的字串。 這些字元不區分大小寫。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)
