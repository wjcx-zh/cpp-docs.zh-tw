---
title: 連結器工具錯誤 LNK1277 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1277
dev_langs:
- C++
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 542c48bd23b3f84ab301404987c77d964f51823e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082510"
---
# <a name="linker-tools-error-lnk1277"></a>連結器工具錯誤 LNK1277

在 pgd (filename) 中找不到物件記錄

使用時[/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)，其中一個輸入的.lib、 def、 或.obj 檔的路徑是不同會有在 /ltcg: pginstrument 時所在的路徑。 這可能會在 /ltcg: pginstrument 之後說明 LIB 環境變數中的變更。 輸入檔的完整路徑儲存在.pgd 檔案。

/Ltcg: pgoptimize 必須與 /ltcg: pginstrument 階段相同的輸入。

若要解決這個警告，請執行下列其中一項：

- 執行 /ltcg: pginstrument、 重做所有測試回合，並執行 /ltcg: pgoptimize。

- 將 LIB 環境變數變更為所執行 /ltcg: pginstrument 時。

不建議您在使用除了解決 LNK1277。