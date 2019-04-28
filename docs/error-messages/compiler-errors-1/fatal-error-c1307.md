---
title: 嚴重錯誤 C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338528"
---
# <a name="fatal-error-c1307"></a>嚴重錯誤 C1307

在收集分析資料時已對程式進行編輯

使用時[/ltcg: pgoptimize](../../build/reference/ltcg-link-time-code-generation.md)、 連結器偵測到輸入的模組 /ltcg: pginstrument 之後已重新編譯和模組已變更為現有的設定檔資料所在不再相關的點。 例如，如果在重新編譯的模組中，變更呼叫歷程圖，則編譯器會產生 C1307。

若要解決這個錯誤，執行 /ltcg: pginstrument、 重做所有測試回合，並執行 /ltcg: pgoptimize。 如果您不能執行 /ltcg: pginstrument 和取消復原所有測試回合，使用 /ltcg: pgoptimize 代替除了，來建立最佳化映像。