---
title: 連結器工具錯誤 LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195418"
---
# <a name="linker-tools-error-lnk1000"></a>連結器工具錯誤 LNK1000

> 未知的錯誤;如需技術支援選項，請參閱檔

請注意錯誤的狀況，然後嘗試找出問題，並建立可重現的測試案例。 如需如何調查和報告這些錯誤的相關資訊，請參閱[如何回報視覺效果C++工具組或檔的問題](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果您混用標準標頭檔（例如，Windows .h）和您自己的檔案，可能會收到這個錯誤。 包含先行編譯的標頭（如果有的話），然後是標準標頭，後面接著您自己的標頭檔。
