---
title: 連結器工具錯誤 LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 8e53dc898addb4adeec63027c358b42a6a836b50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501721"
---
# <a name="linker-tools-error-lnk1000"></a>連結器工具錯誤 LNK1000

> 未知的錯誤;如需技術支援選項，請參閱文件

請注意錯誤的情況下，然後試著找出問題，並建立可重現的測試案例。 如需如何調查與報告這些錯誤的資訊，請參閱[如何回報 Visual c + + 工具組或文件的問題](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果您混合使用標準標頭檔 (例如 Windows.h) 和您自己的檔案，您可能會發生此錯誤。 先行編譯標頭，如果包含任何、 第一個，則標準的標頭，後面加上您自己的標頭檔。