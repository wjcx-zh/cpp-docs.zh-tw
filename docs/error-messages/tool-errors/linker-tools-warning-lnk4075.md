---
title: 連結器工具警告 LNK4075 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4075
dev_langs:
- C++
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a021a9345975dcb197ab578901baf22f76db846
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059650"
---
# <a name="linker-tools-warning-lnk4075"></a>連結器工具警告 LNK4075

正在略過 "option1"，因為 「 option2 」 規格

第二個選項會覆寫第一個。

會指定互斥的連結器選項。  檢查您的連結器選項。  連結器選項指定的位置取決於您如何建置您的專案。

- 如果您要建置開發環境中，尋找您的專案，連結器屬性頁中，並查看 其中這兩個連結器選項所指定。  請參閱[使用專案屬性](../../ide/working-with-project-properties.md)如需詳細資訊。

- 如果您在命令列建置時，查看那里指定的連結器選項。

- 如果您使用建置指令碼來建置，查看您的指令碼，以查看這些連結器選項會指定位置。

當您找到其中指定互斥的連結器選項時，請移除其中一個連結器選項。

某些特定的範例：

- 如果您連結與已編譯的模組 **/ZI**，這表示內部連結器選項呼叫 /EDITANDCONTINUE，並使用 /opt: ref，/opt: icf 或 /incremental: no，已編譯的模組表示沒有 /EDITANDCONTINUE，您將會取得 LNK4075。  請參閱[/z7，/Zi，/ZI （偵錯資訊格式）](../../build/reference/z7-zi-zi-debug-information-format.md)如需詳細資訊。