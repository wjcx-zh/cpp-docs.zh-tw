---
title: 描述區塊
description: NMAKE 使用描述區塊來建立 makefile 中的目標、相依性和命令的關聯。
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: 8f7bf3a26eadde91471e8b45ec26e0abea906244
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506589"
---
# <a name="description-blocks"></a>描述區塊

描述區塊構成 makefile 的核心。 它們會描述要建立目標的 *目標*或 *檔案，以及它們的*相依性所需的檔案。 描述區塊可能包含 *命令*，說明如何從相依性建立目標。 描述區塊是相依性程式列，選擇性地緊接著命令區塊：

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>相依性行

相依性 *行* 指定一個或多個目標，以及零或多個相依項。 如果目標不存在，或具有比相依較早的時間戳記，NMAKE 會執行命令區塊中的命令。 如果目標為 [偽](#pseudotargets)目標，NMAKE 也會執行命令區塊。 以下是相依性行的範例：

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

在此相依性行中， `hi_bye.exe` 是目標。 其相依性為 `hello.obj` 、 `goodbye.obj` 和 `helper.lib` 。 相依性行可告知 NMAKE 在每次 `hello.obj` 、 `goodbye.obj` 或 `helper.lib` 最近變更時建立目標 `hi_bye.exe` 。

目標必須在行首。 它無法以任何空格或定位字元縮排。 使用冒號 (`:`) ，將目標與相依項分開。 目標、冒號分隔符號 () 和相依項之間允許有空格或索引標籤 `:` 。 若要分割相依性行，請使用反斜線 (在 `\` 目標或相依的之後) 。

NMAKE 在執行命令區塊之前，會掃描所有相依性和任何適用的推斷規則，以建立相依性 *樹狀結構*。 相依性樹狀結構會指定完整更新目標所需的步驟。 NMAKE 會以遞迴方式檢查相依性是否為另一個相依性清單中的目標。 在建立相依性樹狀結構之後，NMAKE 會檢查時間戳記。 如果樹狀結構中有任何相依性比目標新，NMAKE 會建立目標。

## <a name="targets"></a><a name="targets"></a> 目標

相依性行的 [目標] 區段會指定一或多個目標。 目標可以是任何有效的檔案名、目錄名稱或 [偽](#pseudotargets)目標。 使用一或多個空格或定位字元來分隔多個目標。 目標不區分大小寫。 允許使用檔案名的路徑。 目標及其路徑不能超過256個字元。 如果冒號之前的目標是單一字元，請使用分隔的空格。 否則，NMAKE 會將字母冒號組合解讀為磁片磁碟機規範。

### <a name="multiple-targets"></a><a name="multiple-targets"></a> 多個目標

NMAKE 會以單一相依性來評估多個目標，就像是在個別的描述區塊中指定每個目標一樣。

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

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a> 累計相依性

當目標重複時，描述區塊中的相依性是累計的。

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

當您在單一描述區塊中的多個相依性行中有多個目標時，NMAKE 會將它們評估為個別的描述區塊中指定的目標。 不過，只有最後一個相依性行中的目標會使用命令區塊。 NMAKE 嘗試使用其他目標的推斷規則。

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

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a> 多個描述區塊中的目標

若要使用不同的命令更新多個描述區塊中的目標，請在目標和相依性之間指定兩個連續的冒號 (：： ) 。

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a> 相依性的副作用

您可以在不同位置的兩個相依性行中指定具有冒號 (： ) 的目標。 如果命令只出現在其中一行，NMAKE 會將相依性解讀為相鄰或合併的行。 它不會叫用沒有任何命令之相依性的推斷規則。 相反地，NMAKE 會假設相依性屬於一個描述區塊，並執行其他相依性所指定的命令。 請考慮這組規則：

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

如果使用雙冒號 () ，就不會發生此效果 `::` 。 例如，這組規則：

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

### <a name="pseudotargets"></a><a name="pseudotargets"></a> Pseudotargets

*偽*物件是用來取代相依性行中之檔案名的標籤。 它會被解釋為不存在的檔案，因此已過期。 NMAKE 假設非目標的時間戳記與其所有相依項的最新。 如果沒有相依性，則會假設為目前的時間。 如果使用子目標做為目標，則一律會執行其命令。 當做相依使用的偽物件也必須顯示為另一個相依性中的目標。 不過，該相依性不需要有命令區塊。

偽目標名稱會遵循目標的檔案名語法規則。 但是，如果名稱沒有副檔名，它可能會超過8個字元的檔案名限制，且長度最多可達256個字元。

當您想要讓 NMAKE 自動建立多個目標時，Pseudotargets 會很有用。 NMAKE 只會建立命令列上指定的目標。 或者，如果未指定任何命令列目標，它只會在 makefile 的第一個相依性中建立第一個目標。 您可以告知 NMAKE 建立多個目標，而不需在命令列上個別列出它們。 撰寫包含子物件之相依性的描述區塊，並列出您想要建立為其相依性的目標。 然後，先將此描述區塊放在 makefile 中，或在 NMAKE 命令列上指定 [偽]。

在此範例中，更新是一個偽目標。

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

評估更新時，NMAKE 會將目前目錄中的所有檔案複製到指定的磁片磁碟機和目錄。

在下列 makefile 中，如果在 `all` `project1.exe` `project2.exe` `all` 命令列上未指定任何目標，則會同時建立和。 在更新檔案之前，目標 `setenv` 會變更 LIB 環境變數 `.exe` ：

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a> 家屬

在相依性程式列中，指定在冒號 () 或雙冒號 () 的零個或多個相依項 `:` `::` ，使用任何有效的檔案名或 [目標](#pseudotargets)物件。 使用一或多個空格或定位字元來分隔多個相依項。 相依項不區分大小寫。 允許使用檔案名的路徑。

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a> 推斷的相依項

除了您在相依性行中明確列出的相依性之外，NMAKE 也可以採用 *推斷的相依*性。 推斷的相依性衍生自推斷規則，並在明確相依性之前評估。 當推斷的相依性比其目標的日期過期時，NMAKE 會叫用相依性的命令區塊。 如果推斷的相依性不存在，或已過期（相較于其本身的相依性），NMAKE 會先更新推斷的相依項。 如需推斷相依項的詳細資訊，請參閱 [推斷規則](inference-rules.md)。

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a> 相依的搜尋路徑

您可以為每個相依指定選擇性的搜尋路徑。 以下是指定一組要搜尋之目錄的語法：

> **{**_directory_ \[ **;**_目錄_...]**}**_相依_

以大括弧括住目錄名稱 (`{ }`) 。 以分號 () 分隔多個目錄 `;` 。 不允許使用空格或索引標籤。 NMAKE 會先在目前的目錄中尋找相依的，然後在目錄清單中尋找指定的順序。 您可以使用宏來指定部分或所有搜尋路徑。 只有指定的相依會使用此搜尋路徑。

#### <a name="directory-search-path-example"></a>目錄搜尋路徑範例

此相依性行說明如何建立搜尋的目錄規格：

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

目標 `reverse.exe` 有一個相依的 `retro.obj` 。 以大括弧括住的清單會指定兩個目錄。 NMAKE 會 `retro.obj` 先在目前的目錄中搜尋。 如果不存在，NMAKE 會搜尋 `\src\omega` 目錄，然後搜尋 `e:\repo\backwards` 目錄。

## <a name="see-also"></a>另請參閱

[NMAKE 參考](nmake-reference.md)
