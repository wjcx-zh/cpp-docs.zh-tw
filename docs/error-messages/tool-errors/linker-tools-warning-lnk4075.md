---
title: 連結器工具警告 LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183484"
---
# <a name="linker-tools-warning-lnk4075"></a>連結器工具警告 LNK4075

忽略 "option1"，因為 "option2" 規格

第二個選項會覆寫第一個。

正在指定互斥的連結器選項。  檢查您的連結器選項。  指定連結器選項的位置取決於您建立專案的方式。

- 如果您是在開發環境中建立，請查看專案的連結器屬性頁，並查看同時指定這兩個連結器選項的位置。  如需詳細資訊，請參閱[設定編譯器和組建屬性](../../build/working-with-project-properties.md)。

- 如果您在命令列中建立，請查看此處指定的連結器選項。

- 如果您使用組建腳本建立，請查看您的腳本，以查看指定這些連結器選項的位置。

當您發現指定了互斥連結器選項的位置時，請移除其中一個連結器選項。

一些特定範例：

- 如果您連結以 **/zi**編譯的模組，這表示名為/EDITANDCONTINUE 的內部連結器選項，以及使用/OPT： REF、/OPT： ICF 或/INCREMENTAL： NO 編譯的模組，則會得到 LNK4075。  如需詳細資訊，請參閱[/Z7、/zi、/zi （Debug 資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md) 。
