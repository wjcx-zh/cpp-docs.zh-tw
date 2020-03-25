---
title: 連結器工具警告 LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: b1f330924b8e47e0649268142106a050c83cb20a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183315"
---
# <a name="linker-tools-warning-lnk4099"></a>連結器工具警告 LNK4099

找不到具有 ' object/library ' 或 ' path ' 的 PDB ' filename ';連結化物件，如同沒有任何調試資訊

連結器找不到您的 .pdb 檔案。 將它複製到包含 `object/library`的目錄中。

若要尋找與物件檔案相關聯的 .pdb 檔案名：

1. 使用[lib](../../build/reference/lib-reference.md) **/extract：** `xyz``objectname`從程式庫將物件檔案**解壓縮。** **.lib**

1. 使用**dumpbin/section：. debug $ T `objectname`/rawdata**檢查 .pdb 檔案的**路徑。**

您也可以使用[/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)進行編譯，因此不需要使用 pdb，或如果您要連結的物件沒有 .pdb 檔案，則移除[/debug](../../build/reference/debug-generate-debug-info.md)連結器選項。
