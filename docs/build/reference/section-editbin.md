---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 8bcc925b34118630c872a0147b93291626b7c19b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318598"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>備註

此選項會變更區段，覆寫區段的物件檔案編譯或連結時所設定的屬性的屬性。

冒號之後 ( **:** )，指定*名稱*的區段。 若要變更的區段名稱，請遵循*名稱*以等號 （=） 和*newname*區段。

若要設定或變更的區段`attributes`，指定逗號 (**，**) 後面接著一或多個屬性的字元。 要變換正負號的屬性，在屬性和一個驚嘆號 （！） 字元前面。 下列字元指定記憶體的屬性：

|屬性|設定|
|---------------|-------------|
|c|程式碼|
|d|可捨棄|
|e|可執行檔|
|i|初始化的資料|
|K|快取的虛擬記憶體|
|m|移除連結|
|o|連結資訊|
|p|分頁的虛擬記憶體|
|r|讀取|
|秒|共用|
|u|未初始化的資料|
|w|寫入|

控制*對齊*，指定的字元**A**後面接著一個，如下所示設定對齊的大小 （位元組），下列字元：

|字元|對齊大小 （位元組）|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|秒|64|
|x|沒有對齊|

指定`attributes`並*對齊*字元視為任何泛空白字元的字串。 這些字元不區分大小寫。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)
