---
title: 描述區塊
description: NMAKE 使用描述塊來關聯 makefile 中的目標、依賴項和命令。
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322255"
---
# <a name="description-blocks"></a>描述區塊

描述塊構成 makefile 的核心。 它們描述*要建立目標所需的*檔案或檔案*及其相依項*。 描述區塊可能包含*命令*,用於描述如何從依賴項創建目標。 描述塊是依賴項行,可選後跟命令塊:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>相依項行

*依賴項行*指定一個或多個目標,以及零個或多個依賴項。 如果目標不存在,或者時間戳早於從屬物件,NMAKE 將執行命令塊中的命令。 如果目標是[偽目標](pseudotargets.md),NMAKE 也會執行命令塊。 下面是依賴項行範例:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

在此依賴項行中`hi_bye.exe`,是目標。 其相依項`hello.obj``goodbye.obj`是`helper.lib`與 。 依賴項`hello.obj`行告訴 NMAKE`goodbye.obj`在`helper.lib`何時 生成目標`hi_bye.exe`,或最近更改比 更改。

目標必須位於行的開頭。 它不能縮進與任何空格或選項卡。 使用冒號`:`() 將目標與依賴項分開。 目標、冒號分隔符 ()`:`和依賴項之間允許空格或選項卡。 要拆分依賴項線,請使用目標或從屬`\`項之後的反斜杠 ( )。

在執行命令塊之前,NMAKE 會掃描所有依賴項和任何適用的推理規則,以產生*依賴項樹*。 依賴項樹指定完全更新目標所需的步驟。 NMAKE 會遞歸地檢查從屬人本身是否是另一個依賴項列表中的目標。 生成依賴項樹後,NMAKE 會檢查時間戳。 如果樹中的任何從屬關係比目標更新,NMAKE 將生成目標。

## <a name="targets"></a><a name="targets"></a>目標

依賴項行的目標部分指定一個或多個目標。 目標可以是任何合法的檔案名稱或[偽目標](pseudotargets.md)。 通過使用一個或多個空格或選項卡分隔多個目標。 目標不區分大小寫。 允許使用檔名的路徑。 目標及其路徑不能超過 256 個字元。 如果冒號前面的目標是單個字元,請使用分隔空格。 否則,NMAKE 會將字母冒號組合解釋為驅動器指定器。

### <a name="multiple-targets"></a><a name="multiple-targets"></a>多個目標

NMAKE 計算單個依賴項中的多個目標,就像每個目標在單獨的描述塊中指定一樣。

例如,此規則:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

評估為:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>累積依賴項

如果重複目標,依賴項在描述塊中累積。

例如,這組規則,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

評估為:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

當單個描述塊中的多個依賴項行中有多個目標時,NMAKE 會像在單獨的描述塊中指定每個目標一樣計算它們。 但是,只有最後一個依賴項行中的目標才使用命令塊。 NMAKE 嘗試對其他目標使用推理規則。

例如,這組規則,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

評估為:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>多個描述區塊中的目標

要使用不同的指令更新多個描述區塊中的目標,請指定兩個連續冒號 (::)在目標和依賴者之間。

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>依賴項副作用

您可以指定具有冒號(:)位於不同位置的兩個依賴項行中。 如果命令只出現在其中一行之後,NMAKE 會解釋依賴項,就像這些行是相鄰的或組合的一樣。 它不為沒有命令的依賴項調用推理規則。 相反,NMAKE 假定依賴項屬於一個描述塊,並執行與其他依賴項指定的命令。 請考慮這組規則:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

評估為:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

如果使用雙冒號`::`( ) ,則不會發生此效果。 例如,這組規則:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

評估為:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>偽目標

*偽目標*是用於代替依賴項行中的檔名的標籤。 它被解釋為不存在的檔,因此已經過時。 NMAKE 假定偽目標的時間戳與其所有從屬項中的最新時間戳相同。 如果沒有依賴變數,則假定當前時間。 如果偽目標用作目標,則始終執行其命令。 用作從屬人的偽目標還必須在另一個依賴項中顯示為目標。 但是,該依賴項不需要具有命令塊。

偽目標名稱遵循目標的檔名語法規則。 但是,如果名稱沒有副檔名,則它可能超過檔名的 8 個字元限制,並且可以長達 256 個字元。

當您希望 NMAKE 自動生成多個目標時,偽目標非常有用。 NMAKE 僅生成命令行上指定的目標。 或者,如果未指定命令行目標,則僅生成 makefile 中第一個依賴項中的第一個目標。 您可以告訴 NMAKE 生成多個目標,而無需在命令列上單獨列出它們。 編寫包含偽目標的依賴項的描述塊,並將要生成的目標列為其依賴項。 然後,首先在 makefile 中放置此描述區塊,或在 NMAKE 命令列上指定偽目標。

在此示例中,UPDATE 是偽目標。

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

計算更新時,NMAKE 將當前目錄中的所有檔案複製到指定的驅動器和目錄。

在下面的 makefile 中`all`,偽`project1.exe``project2.exe`目標將`all`生成兩者 ,如果命令行上指定了任一目標或未指定目標。 偽目標`setenv`在`.exe`更新 檔案之前更改 LIB 環境變數:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>家屬

在依賴項行中,使用任何有效的檔名或[偽目標](pseudotargets.md)`:`指定冒號`::`( ) 或雙冒號 ( ) 之後的零個或多個從屬項。 通過使用一個或多個空格或選項卡分隔多個從屬項。 受撫養人不區分大小寫。 允許使用檔名的路徑。

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>推斷的受撫養人

除了在依賴項行中顯式列出的依賴項外,NMAKE 可以假定*一個推斷的從屬項*。 推斷的從屬關係派生自推理規則,並在顯式依賴項之前求計算。 當推斷的依賴項與其目標相比過期時,NMAKE 將調用依賴項的命令塊。 如果推斷的從屬關係不存在,或與其自己的從屬項相比已經過時,NMAKE 首先更新推斷的受撫養項。 有關推斷依賴變數的詳細資訊,請參閱[推理規則](inference-rules.md)。

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>搜尋從屬人的路徑

您可以為每個從屬者指定可選的搜索路徑。 下面是指定要搜索的目錄集的語法:

> *****_目錄_\[**;**_目錄_...]*****_相依_

將目錄名稱封閉在括號中`{ }`。 使用分號分隔多個目錄`;`。 不允許空格或製表元。 NMAKE 首先在當前目錄中查找從屬項,然後在指定的順序中查找目錄清單中的從屬項。 可以使用宏指定搜索路徑的部件或全部。 只有指定的從屬者使用此搜索路徑。

#### <a name="directory-search-path-example"></a>目錄搜尋路徑範例

此相依項目的範例的範例如何為搜尋建立目錄規範:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

目標`reverse.exe`有一個相`retro.obj`依物件 。 大括弧內的清單指定兩個目錄。 NMAKE`retro.obj`首先 在當前目錄中搜索。 如果不存在,NMAKE 會`\src\omega`搜索 目錄,`e:\repo\backwards`然後搜索 該目錄。

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
