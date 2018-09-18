---
title: 連結器工具警告 LNK4099 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50bdceaba2e72312febec4819b96df334b5398c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025996"
---
# <a name="linker-tools-warning-lnk4099"></a>連結器工具警告 LNK4099

PDB 'filename' 找不到與 '物件/library' 或 'path';如同沒有偵錯資訊般連結物件

連結器找不到.pdb 檔案。 將它複製到目錄，其中包含`object/library`。

若要尋找的物件檔案與相關聯的.pdb 檔案的名稱：

1. 從程式庫擷取的物件檔案[lib](../../build/reference/lib-reference.md) **/擷取：**`objectname`**.obj** `xyz` **.lib**。

1. 請檢查要使用的.pdb 檔的路徑**dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**。

您也可以使用編譯[/z7](../../build/reference/z7-zi-zi-debug-information-format.md)，因此不需要使用，或移除之 pdb [/ 偵錯](../../build/reference/debug-generate-debug-info.md)連結器選項，如果您還沒有您所連結之物件的.pdb 檔案。