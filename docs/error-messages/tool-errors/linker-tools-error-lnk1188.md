---
title: 連結器工具錯誤 LNK1188 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1188
dev_langs:
- C++
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36b31590d94d809c16ed64d16071db0919f60238
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098936"
---
# <a name="linker-tools-error-lnk1188"></a>連結器工具錯誤 LNK1188

BADFIXUPSECTION:: 無效的修復目標 'symbol';可能為零長度區段

VxD 連結期間的重新放置目標沒有一節。 使用 LINK386 （較舊版本），（MASM 群組指示詞所產生） 的 OMF 群組記錄可能已用來結合區段的另一個非零長度的零長度區段。 COFF 格式不支援在 GROUP 指示詞和長度為零的區段。 當連結會自動將此類型的 OMF 物件轉換成 COFF 時，可能會發生此錯誤。