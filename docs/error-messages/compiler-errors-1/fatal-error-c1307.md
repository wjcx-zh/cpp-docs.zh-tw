---
title: 嚴重錯誤 C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203342"
---
# <a name="fatal-error-c1307"></a>嚴重錯誤 C1307

在收集分析資料時已對程式進行編輯

使用[/ltcg： PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)時，連結器偵測到在/LTCG： PGINSTRUMENT 之後重新編譯的輸入模組，而且該模組已變更為現有的設定檔資料不再相關的時間點。 例如，如果在重新編譯的模組中變更了呼叫圖形，編譯器將會產生 C1307。

若要解決這個錯誤，請執行/LTCG： PGINSTRUMENT、取消復原所有測試回合，然後執行/LTCG： PGOPTIMIZE。 如果您無法執行/LTCG： PGINSTRUMENT 和取消復原所有測試回合，請使用/LTCG： PGUPDATE，而不是/LTCG： PGOPTIMIZE 來建立優化的映射。
