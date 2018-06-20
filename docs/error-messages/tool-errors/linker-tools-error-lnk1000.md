---
title: 連結器工具錯誤 LNK1000 |Microsoft 文件
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a01db36200995813ec4b6862e9ddd04c6f069ba
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238678"
---
# <a name="linker-tools-error-lnk1000"></a>連結器工具錯誤 LNK1000

> 未知的錯誤。如需技術支援選項，請參閱文件

請注意錯誤的情況下，然後再次嘗試以隔離問題，並建立可重現的測試案例。 如何調查，並報告這些錯誤的資訊，請參閱[如何報告問題的 Visual c + + 工具組或文件](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

如果您混用標準標頭檔 (例如，Windows.h) 與您自己的檔案，您可能會收到這個錯誤。 如果任何，第一個，然後標準標頭，後面接著您自己的標頭檔，請包含先行編譯標頭。