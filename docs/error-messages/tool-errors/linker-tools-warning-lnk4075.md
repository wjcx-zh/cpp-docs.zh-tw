---
title: 連結器工具警告 LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bf22e7c78dce6949c357d7ad4a0c76209c88eef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186901"
---
# <a name="linker-tools-warning-lnk4075"></a>連結器工具警告 LNK4075

正在略過 "option1"，因為 「 option2 」 規格

第二個選項會覆寫第一個。

會指定互斥的連結器選項。  檢查您的連結器選項。  連結器選項指定的位置取決於您如何建置您的專案。

- 如果您要建置開發環境中，尋找您的專案，連結器屬性頁中，並查看 其中這兩個連結器選項所指定。  請參閱[設定編譯器和組建屬性](../../build/working-with-project-properties.md)如需詳細資訊。

- 如果您在命令列建置時，查看那里指定的連結器選項。

- 如果您使用建置指令碼來建置，查看您的指令碼，以查看這些連結器選項會指定位置。

當您找到其中指定互斥的連結器選項時，請移除其中一個連結器選項。

某些特定的範例：

- 如果您連結與已編譯的模組 **/ZI**，這表示內部連結器選項呼叫 /EDITANDCONTINUE，並使用 /opt: ref，/opt: icf 或 /incremental: no，已編譯的模組表示沒有 /EDITANDCONTINUE，您將會取得 LNK4075。  請參閱[/z7，/Zi，/ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)如需詳細資訊。