---
title: 連結器工具錯誤 LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 7c00fb32e4b36eff119195efbb34d536d80df6a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183653"
---
# <a name="linker-tools-error-lnk1277"></a>連結器工具錯誤 LNK1277

在 pgd （filename）中找不到物件記錄

使用[/ltcg： PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)時，其中一個輸入 .lib、def 或 .obj 檔案的路徑與在/LTCG： PGINSTRUMENT 中找到它們的路徑不同。 這可能是因為在/LTCG： PGINSTRUMENT 之後，LIB 環境變數中的變更所述。 輸入檔的完整路徑會儲存在 .pgd 檔案中。

/LTCG： PGOPTIMIZE 要求輸入必須與/LTCG： PGINSTRUMENT 階段相同。

若要解決這個警告，請執行下列其中一項動作：

- 執行/LTCG： PGINSTRUMENT、取消復原所有測試回合，並執行/LTCG： PGOPTIMIZE。

- 將 LIB 環境變數變更為執行/LTCG： PGINSTRUMENT 時的功能。

不建議您使用/LTCG： PGUPDATE 來解決 LNK1277。
