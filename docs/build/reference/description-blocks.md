---
title: 描述區塊
description: NMAKE 會使用描述區塊，在 makefile 中關聯目標、相依性和命令。
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144529"
---
# <a name="description-blocks"></a>描述區塊

描述區塊會形成 makefile 的核心。 它們會描述*目標*，或要建立的*檔案及其相依性，建立*目標所需的檔案。 描述區塊可能包含*命令*，描述如何從相依性建立目標。 描述區塊是相依性行，可選擇性地後面接著命令區塊：

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>相依性行

相依性*行會*指定一個或多個目標，以及零或多個相依性。 如果目標不存在，或具有比相依的更早時間戳記，則 NMAKE 會執行命令區塊中的命令。 如果目標是「[偽](pseudotargets.md)」，則 NMAKE 也會執行命令區塊。 以下是相依性行的範例：

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

在此相依性程式程式碼中，`hi_bye.exe` 為目標。 其相依性為 `hello.obj`、`goodbye.obj`和 `helper.lib`。 當 `hello.obj`、`goodbye.obj`或 `helper.lib` 變更最近超過 `hi_bye.exe`時，相依性行會告訴 NMAKE 建立目標。

目標必須在行的開頭。 它不能以空格或索引標籤縮排。 使用冒號（`:`）來分隔相依性的目標。 目標、冒號分隔符號（`:`）和相依性之間允許使用空格或索引標籤。 若要分割相依性行，請在目標或相依的後面使用反斜線（`\`）。

在執行命令區塊之前，NMAKE 會掃描所有相依性和任何適用的推斷規則，以建立相依性*樹狀結構*。 相依性樹狀結構指定完整更新目標所需的步驟。 NMAKE 會以遞迴方式檢查相依本身是否為另一個相依性清單中的目標。 在建立相依性樹狀結構之後，NMAKE 會檢查時間戳記。 如果樹狀結構中的任何相依性比目標新，NMAKE 會建立目標。

## <a name="targets"></a> 目標

相依性行的 [目標] 區段會指定一或多個目標。 目標可以是任何有效的檔案名、目錄名稱或[偽](pseudotargets.md)目標。 使用一或多個空格或索引標籤來分隔多個目標。 目標不會區分大小寫。 允許使用檔案名的路徑。 目標及其路徑不能超過256個字元。 如果冒號前面的目標是單一字元，請使用分隔空間。 否則，NMAKE 會將字母冒號組合解讀為磁片磁碟機規範。

### <a name="multiple-targets"></a>多個目標

NMAKE 會在單一相依性中評估多個目標，如同個別的描述區塊中所指定。

例如，此規則：

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

評估為：

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>累計相依性

當目標重複時，相依性會累積在描述區塊中。

例如，這組規則，

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

評估為：

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

當您在單一描述區塊的多個相依性程式列中有多個目標時，NMAKE 會依照個別描述區塊中指定的順序來評估它們。 不過，只有最後一個相依性程式列中的目標使用命令區塊。 NMAKE 會嘗試針對其他目標使用推斷規則。

例如，這組規則，

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

評估為：

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>多個描述區塊中的目標

若要使用不同的命令來更新多個描述區塊中的目標，請指定兩個連續的冒號（：:)在目標和相依項之間。

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>相依性的副作用

您可以指定具有冒號的目標（:)在不同位置的兩個相依性行中。 如果命令只會出現在其中一行之後，NMAKE 會解讀相依性，就像行相鄰或合併的一樣。 它不會針對沒有命令的相依性叫用推斷規則。 相反地，NMAKE 會假設相依性屬於一個描述區塊，並執行以其他相依性指定的命令。 請考慮這組規則：

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

評估為：

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

如果使用雙冒號（`::`），則不會發生這種效果。 例如，這組規則：

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

評估為：

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>Pseudotargets

「*偽*物件」是用來取代相依性行中檔案名的標籤。 它會被解讀為不存在的檔案，因此已過期。 NMAKE 假設偽目標的時間戳記與其所有相依項的最新。 如果沒有相依性，則會假設為目前的時間。 如果使用偽目標作為目標，則一律會執行其命令。 當做相依使用的偽物件也必須顯示為另一個相依性中的目標。 不過，這項相依性不需要有命令區塊。

「偽」名稱遵循目標的檔案名語法規則。 不過，如果名稱沒有副檔名，它可能會超過8個字元的檔案名限制，而且長度最多可達256個字元。

當您希望 NMAKE 自動建立一個以上的目標時，Pseudotargets 會很有用。 NMAKE 只會建立在命令列上指定的目標。 或者，如果未指定任何命令列目標，它只會在 makefile 的第一個相依性中建立第一個目標。 您可以指示 NMAKE 建立多個目標，而不需要在命令列上個別列出它們。 撰寫具有包含偽物件之相依性的描述區塊，並列出您想要建立其相依性的目標。 然後，先將此描述區塊放在 makefile 中，或在 NMAKE 命令列上指定偽目標。

在此範例中，UPDATE 是一個偽目標。

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

評估更新時，NMAKE 會將目前目錄中的所有檔案複製到指定的磁片磁碟機和目錄。

在下列 makefile 中，如果 `all` 或未在命令列上指定任何目標，則偽目標 `all` 會同時建立 `project1.exe` 和 `project2.exe`。 在更新 `.exe` 檔案之前，偽目標 `setenv` 會變更 LIB 環境變數：

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>相關性

在相依性程式程式碼中，使用任何有效的檔案名或[偽](pseudotargets.md)物件，指定冒號（`:`）或雙冒號（`::`）後面的零個或多個相依項。 使用一或多個空格或索引標籤來分隔多個相依項。 相依項不區分大小寫。 允許使用檔案名的路徑。

### <a name="inferred-dependents"></a>推斷的相依項

除了您在相依性行中明確列出的相依性之外，NMAKE 也可以假設有*推斷的相依*性。 推斷的相依性是衍生自推斷規則，而且會在明確依存項之前評估。 相較于其目標，當推斷的相依項已過期時，NMAKE 會叫用命令區塊來進行相依性。 如果推斷的相依性不存在，或相較于它自己的相依性，則 NMAKE 會先更新推斷的相依性。 如需推斷相依項的詳細資訊，請參閱[推斷規則](inference-rules.md)。

### <a name="search-paths-for-dependents"></a>相依性的搜尋路徑

您可以為每個相依的指定選擇性搜尋路徑。 以下是指定一組要搜尋之目錄的語法：

> **{** _directory_\[ **;** _目錄_...] **}** _相依_

以大括弧括住目錄名稱（`{ }`）。 以分號分隔多個目錄（`;`）。 不允許空格或索引標籤。 NMAKE 會先在目前目錄中尋找相依項，然後在目錄清單中，依照指定的順序。 您可以使用宏來指定部分或全部的搜尋路徑。 只有指定的相依使用此搜尋路徑。

#### <a name="directory-search-path-example"></a>目錄搜尋路徑範例

這一行顯示如何建立搜尋的目錄規格：

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

目標 `reverse.exe` 有一個相依的 `retro.obj`。 以大括弧括住的清單會指定兩個目錄。 NMAKE 會先在目前的目錄中搜尋 `retro.obj`。 如果沒有這麼做，NMAKE 會搜尋 `\src\omega` 目錄，然後搜尋 `e:\repo\backwards` 目錄。

## <a name="see-also"></a>請參閱

[NMAKE 參考](nmake-reference.md)
